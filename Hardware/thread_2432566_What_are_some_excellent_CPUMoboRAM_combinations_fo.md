---
title: "What are some excellent CPU/Mobo/RAM combinations for Ub 18, 20+ o/s' ?"
date: 2019-12-04
forum: Hardware
---

### Post by ra7411 on 2019-12-04
The title says it.  Any ideas / opinions?

This would be for a desktop, mostly for routine video / audio processing non-gaming applications.

Thanks

---

### Post by TheFu on 2019-12-04
Budget?  What will you reuse?  Wifi important or undesirable? GigE?  Multiple NICs?  How much RAM?

To start ball-park budgets, I use **pcpartpicker.com** to filter on things I consider mandatory. Often, I'll need to relax some of those requirements.  After narrowing down each part, I'll start searching Linux forums for issues that weren't easily solved.

Last year, I upgraded a system with new MB+CPU+RAM+GPU and an SSD.  I'd been reading about Ryzen for a few years and new the price/performance for my multi-threaded workloads was with Ryzen.  But I wanted to keep power use as low as possible, so I avoided the 95W ryzen models (the ones with an X) in the name.  I wanted 12 cores or more ... so a Ryzen 1600/2600/3600  or better was needed.  It had been years since I'd bought any GPU. The built-in iGPU graphics that Intel provides has been great, so I looked at a similar Core i5. The price was about $80 more and it had fewer cores and was slightly slower overall.

I'm also an Intel-NIC person for many reasons.  Any motherboards that don't use Intel NICs are off my list.  Just too many issues with others so if paying $10 more avoids those issues, great.  Intel also has their NICs do more processing than the others like Realtek, so fewer interrupts means more network speed with less CPU overhead.  I didn't want wifi. I consider wifi a security liability.  

This NIC requirement really pushed me to Asus ROG boards. There is the MB I dream about and the MB I want to afford. Those are often $200 apart.  Plus RAM was much more expensive a year ago and Ryzen is sensitive to slow RAM, so getting 3200 or faster is strongly recommended.  I've used Ripsaws for years and never had issues.  It was $140 for 16G of 3200 Ripsaws DDR4 12 months ago.  Today, that same RAM is less than $60.

Around here, Microcenter has nicely priced motherboard+CPU bundles, but they are in-store only.  Usually at least $20 less than any other online retailer with the bundle price, so looking through those deals will quickly reduce the available MB options for more research.

So, 12 months ago, I built a Ryzen 5 2600 + Asus ROG STRIX B450-F GAMING + Ripsaws 3200 DDR4 system.  
Sure, I'd like to have a X570  motherboard, but not for $200 more.

And 1 gotcha - know the exact configuration of any NVMe storage supported.  My B450 supports 2 NMVe, but only one is at x4 speeds and if either is used, SATA5/SATA6 ports stop working.  That's pretty common. I had to buy an extra PCIe  HBA to support some extra disks.

---

### Post by ra7411 on 2019-12-04
Oh my god - :D

I wasn't very explicit - this just for a routine desktop, assemble it myself, occasional  re-coding of vid files, playing vids, editing vids and audio, doing spreadsheets, mostly mundane usage.  Cost isn't a big deal but maybe circa $500 or less would be fine - I don't really need a third desktop, but what the hell.....

I have been thinking about a Ryzen, posted a question in here:  "AMD Ryzen running Ub 18.04?"  
 and got alerted to some potential problems, so I figured I'd try to get advice about a CPU/Mobo/RAM combination that doesn't have problems with Ub 18.04 and what is likely to be 20.04.

Thanks

---

### Post by TheFu on 2019-12-04
_Routine desktop_ is highly subjective.

I run 16.04 on my Ryzen 2600, but that's more about my dislike of 18.04 systemd, netplan, and other changes than ryzen.
There haven't been any Ryzen issues in some time - perhaps you are confusing iGPU issues with Ryzen?  Avoid the newest Ryzen models with integrated graphics.

You can get a Ryzen 1600 + cheap B450 MB + 16G of RAM for about $230.  That's over 11,000 passmarks.  Is a 40% loss of performance worth getting a Ryzen 2400g ; 7500 passmarks (with iGPU?)?  these two CPUs are effectively the same price today.

If you don't need a desktop, why not build a DAS/NAS server?  For transcoding videos, you'll still want a Ryzen. 8 min or less to transcode a 43 min recording - I remove commercials.  A 3.6GB file (with commercials already removed) is 0.96GB after transcoding to 720p.

---

### Post by Dennis N on 2019-12-04
Have you looked at PCPartPicker?
[https://pcpartpicker.com/](https://pcpartpicker.com/)

View sample builds (with parts list) like:
[https://pcpartpicker.com/guide/4Wv6Mp/budget-homeoffice-build](https://pcpartpicker.com/guide/4Wv6Mp/budget-homeoffice-build)

or using System Builder Link, You can start with a CPU, and find hundreds of combinations of compatable components.

---

