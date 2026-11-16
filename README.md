# OVH Alternatives: Which Vultr Plan Do You Need, What Did OVH Really Raise, and How Do You Migrate Without an Outage? (Full Plan and Price Table)

OVHcloud's new bare metal prices took effect on 1 September, and the increase is not one number: about **+28% on Gen 2024 configurations**, **+51% on Gen 2026**, up to **+59% on High Grade** and **+87% on the Game range**. From 1 October, Public Cloud bills IPv4 addresses and Low Latency Block Storage as separate line items, which lands at roughly **+1.4% to +21.9% per instance** depending on how many IPs and volumes it carries. If either change hits your invoice, Vultr is worth pricing against your current setup: Cloud Compute starts at **$2.50/month**, everything bills hourly with a monthly cap, and the network covers 33 data center regions.

Below you'll find every Vultr product family with its entry configuration and price, the exact breakdown of what OVH raised and which customers escaped it, a way to check your own bill before you shop, and a migration sequence whose test run costs about €0.27.

> **Most readers should start here.** The $2.50 Cloud Compute tier is a 0.5 GB IPv6-only test box, not a place to put a database-backed site. For a real workload, the 1 GB Regular instance at $5/month or the $6 High Performance tier (NVMe, EPYC or Xeon) is the sensible entry point. 👉 [Check Vultr's current plan lineup and the $300 new-account credit](https://bit.ly/VuLtr)

## Every Vultr product family, with entry prices

Vultr sells seven compute families plus bare metal and GPU. Entry prices span two orders of magnitude, and the gap between the $2.50 tier and the $6 tier buys you a different class of hardware, not just more RAM.

| Plan family | Hardware | Entry configuration | Entry price and billing | Order |
| --- | --- | --- | --- | --- |
| Cloud Compute – Regular Performance | Shared previous-gen Intel, regular SSD | 1 vCPU / 0.5 GB / 10 GB, **IPv6 only** | $2.50/mo (≈$0.004/hr), hourly with monthly cap | [Start on the $2.50 tier](https://bit.ly/VuLtr) |
| Cloud Compute – High Performance | Shared AMD EPYC or Intel Xeon, NVMe | from $6.00/mo | Hourly, monthly cap | [Compare High Performance plans](https://bit.ly/VuLtr) |
| Cloud Compute – High Frequency | Intel Xeon at 3 GHz+, NVMe | 10 sizes, $6 to $320/mo | Hourly, monthly cap | [See High Frequency sizes](https://bit.ly/VuLtr) |
| VX1 | Dedicated AMD EPYC cores (launched October 2025) | Configured at order | Hourly | [Check VX1 availability](https://bit.ly/VuLtr) |
| Optimized – General Purpose | Dedicated vCPU, AMD EPYC, NVMe | from $30.00/mo | Hourly, monthly cap | [View General Purpose plans](https://bit.ly/VuLtr) |
| Optimized – CPU Optimized | Dedicated vCPU, AMD EPYC, NVMe | from $28.00/mo | Hourly, monthly cap | [View CPU Optimized plans](https://bit.ly/VuLtr) |
| Optimized – Memory Optimized | Dedicated vCPU, AMD EPYC, NVMe | from $40.00/mo | Hourly, monthly cap | [View Memory Optimized plans](https://bit.ly/VuLtr) |
| Optimized – Storage Optimized | Dedicated vCPU, AMD EPYC, NVMe | from $75.00/mo | Hourly, monthly cap | [View Storage Optimized plans](https://bit.ly/VuLtr) |
| Bare Metal | Whole physical servers, no virtualization layer | Configured at order | Hourly or monthly | [See bare metal configurations](https://bit.ly/VuLtr) |
| Cloud GPU | NVIDIA GH200 and H100 | GH200 at $4.335/hr, H100 at $19.988/hr | Hourly | [Check GPU availability](https://bit.ly/VuLtr) |

Each family has several sizes; the prices above are the entry point of each line, and the full size list sits on Vultr's pricing page.

Three details decide whether the cheap tier is actually cheap for you:

**The $2.50 plan has no IPv4 address.** It ships IPv6 only. If any part of your stack assumes a v4 address (an old monitoring agent, a payment provider's callback whitelist, a game server), that $2.50 becomes a $2.50 plan plus whatever workaround you build.

**Bandwidth is pooled at account level but accrues hourly.** Vultr includes 2 TB of free egress per account, inbound traffic is free, and overage runs $0.01/GB. The monthly allowance for each instance is added hour by hour at one-six-hundred-seventy-second of its monthly cap, so a large outbound burst in the first days of the month can exceed what has accrued and trigger overage before the pool fills up.

**Hourly billing has a monthly ceiling.** Run an instance for the whole month and you pay the monthly price, not 730 times the hourly rate. That ceiling is what makes hourly billing safe for permanent workloads and useful for short-lived ones.

## What OVH actually raised, and who escaped it

Four bare metal bands moved on 1 September for new orders, and the headline +87% applies to exactly one of them: the Game range on Gen 2026 hardware. Most affected customers face +28% or +51%.

| OVHcloud range | Change | Effective |
| --- | --- | --- |
| Bare metal, Gen 2024 configurations | +28% average | New orders from 1 Sept |
| Bare metal, Gen 2026 configurations | +51% average | New orders from 1 Sept |
| Bare metal, High Grade | up to +59% | New orders from 1 Sept |
| Bare metal, Game (Gen 2026) | +87% | New orders from 1 Sept |
| Already-installed bare metal | Smaller rise, applied at renewal | From 1 Oct |
| Public Cloud instances | IPv4 and Low Latency Block Storage billed separately (+1.4% to +21.9%) | From 1 Oct |
| Managed Databases, Analytics | +3.6% average | From 1 Oct |
| Kimsufi, So You Start, Rise | Unchanged | — |
| Object Storage, MongoDB, HA Block, File Storage | Unchanged | — |

Two groups have little reason to move. If your servers sit on Kimsufi, So You Start or Rise, nothing changed. If you run Public Cloud instances with one IP and no attached volumes, the October change is close to zero for you.

For everyone else, the renewal date matters more than the announcement. Installed bare metal reprices at renewal from 1 October at a smaller rate than new orders, so a machine renewing in December gives you roughly three months to migrate on your own schedule, while a machine renewing on 2 October gives you a weekend.

## Count your IPs before you compare prices

The Public Cloud change is a repackaging, and repackaging rewards tidiness. Your October bill is driven by how many IPv4 addresses and Low Latency Block Storage volumes each instance carries, so unused Failover IPs and orphaned volumes you forgot about are now visible costs. Delete them first, then compare quotes. An instance that keeps one IP and no volumes barely moves; one that accumulated four IPs and three volumes across experiments can land near the top of that +21.9% band.

One more number to keep in view while shopping: OVH's own VPS-1 (2 vCore, 4 GB, 40 GB NVMe) still starts at **€3.81/month ex VAT** when you pay 12 months upfront, and VPS plans carry no hourly billing. On sticker price alone, several alternatives below are more expensive than what you're leaving.

That's not an argument for staying. It's an argument against switching purely on price. Hetzner, netcup and Scaleway all repriced in 2026 too, because every provider buys from the same DDR5 and NVMe market. A migration motivated only by a cheaper monthly figure tends to end in the same search twelve months later. A migration motivated by support response times, API quality, region coverage or billing granularity tends to stick.

## Where Vultr fits, and where it doesn't

Vultr's case rests on three things: a low entry price with real hourly billing, a wide region map, and a console that reviewers find easier to navigate than OVH's.

On coverage, 33 data center regions across six continents is the practical answer to OVH's Eurocentric footprint. If your users are in Singapore, São Paulo or Sydney and your servers aren't, that gap shows up as latency you can measure.

On the buying experience, G2 reviewers comparing the two rate Vultr around 4.3 stars and describe it as easier to do business with, better at support and easier to set up than OVHcloud. Those are comparative judgments from a review platform whose OVHcloud sample sits at 3.0/5 from 79 reviews, not benchmark results.

The counterweight is worth stating plainly. HostDuel's aggregate scoring puts Vultr at 3.8/5 and records a Trustpilot rating of 2.0/5 alongside it, the same weak spot it flags for Linode. Two platforms, two methodologies, two different numbers; the honest reading is that satisfaction is uneven and support quality is the recurring complaint. Vultr also sells unmanaged infrastructure, so there's no control panel and nobody to fix your PHP config. If what you actually want is hand-holding, none of the providers in this article are that.

At common sizes the pricing is competitive: a Regular Performance instance with 2 vCPU, 4 GB and 80 GB runs **$20/month**, against roughly $24 for a comparable DigitalOcean Basic Droplet as listed in October. 👉 [See what the 4 GB Vultr tier costs today](https://bit.ly/VuLtr)

## What the other OVH alternatives cost

These are entry plans read from each provider's own pricing page on 4 September, converted to a common shape. Compare cost per GB of RAM, not the monthly headline, because the entry specs differ wildly (1 to 4 vCPU, 512 MB to 8 GB).

| Provider | Entry plan | Entry price | Metering rule | EU locations |
| --- | --- | --- | --- | --- |
| Hetzner Cloud (Germany) | CX23: 2 vCPU / 4 GB / 40 GB NVMe / 20 TB traffic | €5.49/mo or €0.0088/hr ex VAT; IPv4 billed separately since 15 June | Hourly, rounded up; billed until deleted, not until powered off; monthly cap | Falkenstein, Nuremberg, Helsinki |
| netcup (Germany) | VPS 500 G12: 2 vCore / 4 GB DDR5 ECC / 128 GB NVMe | €5.91/mo incl. 19% VAT on a 12-month term, or €0.010/hr with no term | Monthly contract or hourly | Nuremberg, Vienna, Amsterdam |
| Scaleway (France) | DEV1-S: 2 vCPU / 2 GB | €0.00898/hr (≈€6.55/mo) ex VAT | Hourly pay-as-you-go | Paris, Amsterdam, Warsaw |
| Contabo (Germany) | Cloud VPS 4: 4 cores / 8 GB / 100 GB SSD | €5.50/mo promotional for the first 24 months | Monthly only, no hourly option | Munich, Nuremberg, plus non-EU regions |
| DigitalOcean (US) | Basic: 1 vCPU / 512 MiB / 10 GiB | $4/mo or $0.00595/hr | Per-second, 60-second minimum, monthly cap | Amsterdam, Frankfurt, London |
| OVHcloud (reference) | VPS-1: 2 vCore / 4 GB / 40 GB NVMe | from €3.81/mo ex VAT, 12 months upfront | Monthly or annual, no hourly on VPS | France, Germany, Poland, UK, plus global |

Reading across the rows:

**Most RAM per euro on a commitment:** Contabo's promotional €5.50 buys 8 GB, and netcup's €5.91 including VAT buys 4 GB of DDR5 ECC with 128 GB NVMe. Contabo's rate is promotional for 24 months and monthly-only, so budget for the renewal and for the lack of hourly flexibility.

**Cleanest hourly billing with no minimum term:** Scaleway and netcup's no-term option. Hetzner rounds up to the hour and bills until you delete the server, which matters if you spin up machines and then power them off expecting the meter to stop.

**German data protection and EU jurisdiction:** Hetzner, netcup and Scaleway are all EU-headquartered with EU-only regions in this table. DigitalOcean's US parentage puts it under the CLOUD Act, which is a compliance question rather than a performance one.

**Phone support:** none of the above except through paid tiers. If that's the requirement, the shortlist changes entirely.

## A migration you can test for €0.27

**1. Count IPv4 addresses and block volumes on every instance.** From 1 October these drive your Public Cloud bill. Remove unused Failover IPs and orphaned volumes so you're comparing the real number.

**2. Find your renewal dates.** Installed bare metal reprices at renewal from 1 October at the lower rate. A December renewal buys three months; an early-October renewal does not.

**3. Export everything and test a restore on the target.** Database dumps, object storage sync, configuration in git. Restore once on the new host before cutover day, not during it.

**4. Drop DNS TTLs to 300 seconds at least 24 hours ahead.** Your OVH-assigned IPs stay with OVH; only an address block you own (a /24) can follow you to another provider via BYOIP. Everyone else switches by DNS, which means mail reputation and partner whitelists need checking separately from the website.

**5. Run both setups in parallel for 24 to 48 hours.** On hourly billing, two days of a €4/month shape costs about €0.27. Watch error rates for a day after cutover, then cancel at the end of the paid term. Cancelling mid-term forfeits what you already paid and gains nothing.

## FAQ

**Is Vultr cheaper than OVHcloud?**

Not universally. Vultr's entry point is $2.50/month and a 4 GB instance is $20/month, but OVH's VPS-1 at €3.81/month ex VAT with an annual commitment is still cheaper on sticker for a 4 GB box. Vultr wins on hourly granularity, region count and, according to G2 reviewers, on ease of use and support. If your OVH bill rose by less than 5%, the migration almost certainly costs more than it saves.

**Does hourly billing stop when I power the server off?**

Depends on the provider, and this is where budgets break. Hetzner bills until you delete the server, not until you shut it down. Contabo has no hourly option at all. OVH VPS plans don't bill hourly. DigitalOcean bills per second with a 60-second minimum. Vultr bills hourly with a monthly cap, which is the model that suits CI runners and preview environments.

**Can I take my OVH IP addresses with me?**

Only if you own the block. Addresses OVH allocated to you stay with OVH; a /24 you own can be moved to another provider that supports BYOIP. For everyone else it's a DNS cutover, with the mail reputation and whitelist work that implies.

**How does the $300 Vultr credit work?**

Vultr's coupon page lists a $300 free credit code for new customers, alongside $200 and $250 variants and a deposit-match offer. The restrictions printed with those offers: new customers only, select products only, no combining with other offers, and the credit expires 30 days after signup rather than 30 days after first use. When it expires, billing switches to your linked payment method automatically, so tear down test instances before the clock runs out. A $300 credit over 30 days covers a lot of testing; it isn't three years of a $2.50 instance. 👉 [Read the current credit terms before you sign up](https://bit.ly/VuLtr)

**Which OVH alternative is cheapest per GB of RAM?**

On a 12-month commitment, Contabo's promotional €5.50 for 8 GB and netcup's €5.91 including VAT for 4 GB of DDR5 ECC come out ahead. On flexible hourly billing, Scaleway's DEV1-S at €0.00898/hr and Vultr's $6 High Performance tier are the ones to price against each other.

## Picking by situation

**One small VPS running a site or an API:** Vultr's 1 GB Regular at $5/month, or the $6 High Performance tier if the site touches a database. Skip the $2.50 tier unless you genuinely don't need IPv4.

**CI runners, preview environments, anything that lives for hours:** hourly billing with a monthly cap is the whole decision. Vultr and Scaleway both fit; Hetzner's round-up-to-the-hour rule and Contabo's monthly-only model don't.

**EU data sovereignty as a hard requirement:** compare Hetzner, netcup and Scaleway directly, and put the jurisdiction question to any US-based provider before you sign.

**Users spread across continents:** 33 Vultr regions is the widest map in this comparison, and region proximity is the one performance factor you can't fix with a bigger instance.

Two things to confirm before you enter a card anywhere: whether the plan includes an IPv4 address, and what the monthly cap is, since that's what you'll pay in a normal month. Then run the parallel test. €0.27 for two days of evidence beats a week of guessing. 👉 [Start with Vultr's hourly plans and the $300 credit](https://bit.ly/VuLtr)
