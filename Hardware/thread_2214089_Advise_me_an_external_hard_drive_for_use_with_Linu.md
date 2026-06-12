---
title: "Advise me an external hard drive for use with Linux"
date: 2014-03-30
forum: Hardware
---

### Post by Nickolai_Leschov on 2014-03-30
I am running Ubuntu 13.10 on [ThinkPad X200]("http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-73156") with [Intel 520]("http://www.intel.com/content/www/us/en/solid-state-drives/solid-state-drives-520-series.html") SSD, and I'm going to buy a Microsoft [sic!] [Surface Pro 2]("http://www.microsoft.com/surface/en-us/products/surface-pro-2") (it has USB3) to use with Ubuntu 14.04 and beyond.

So my main hard drive is relatively small but fast SSD and I will need a larger HDD for backups and whatever stuff I'd like to put there. I guess I guess if my main drive is SSD, large external SSD would be ideal, but that's too expensive.

Which external hard drive would you recommend? I am open to both ready-made devices (e.g. WD Passport) and separate pieces (HDD+enclosure). I have an older black USB IDE Agestar box and, while it is probably considered off-brand, works fine for me, though probably slow by today's standards.

Also, which files system should I use on my external drive? Should I use FAT32, to be able to boot from this drive and transfer files to Windows computers?

---

### Post by leclerc65 on 2014-03-30
I use mostly WD drives and I found that the ones with their own power supply are more reliable.
With FAT32, you can occasionally have problem with files larger than 4G.

---

### Post by houstonbofh on 2014-03-30
Have you considered network attached storage?  You can have Windows, and Linux compatibility and still use ext4fs, or you can build a nas4free box and use zfs.  Or just buy one and use whatever it uses and not worry about it.

But if you go USB, avoid the passports.  They have a hidden virtual cd partition that is surprisingly hard to remove.  You are better off whiteboxing it with an enclosure and drive of choice.

---

### Post by Nickolai_Leschov on 2014-05-03
> **houstonbofh said:**
> Have you considered network attached storage?  You can have Windows, and Linux compatibility and still use ext4fs, or you can build a nas4free box and use zfs.  Or just buy one and use whatever it uses and not worry about it.
I just might. So, instead of wired USB, I will connect by wired Ethernet? Wi-Fi is too slow. To think of it, maybe it will have the USB option, too.
Would you recommend any particular network attached storage device? I'm aiming at the compact form factor; the more compact, the better (ideally, close to 2,5" hard drive).
> **houstonbofh said:**
> But if you go USB, avoid the passports.  They have a hidden virtual cd partition that is surprisingly hard to remove.
Thanks for the advice!
> **houstonbofh said:**
> You are better off whiteboxing it with an enclosure and drive of choice.
ok, I was considering it anyway. Any particular recommendations for enclosure? I think I'll go with this one as a drive:
[HGST Travelstar 2.5-Inch 1TB 7200RPM SATA 6GB/s 32MB Cache]("http://smile.amazon.com/HGST-Travelstar-2-5-Inch-7200RPM-Mobile/dp/B0097LG9U8/ref=nosim?tag=793775876-20")
I like my black Agestar IDE enclosure. While it's kinda off-brand, it worked fine for me, looks plain and nice, just the way I like, and takes up hardly more space than a 2.5" hard drive that fits in it (inside a thin metal box there's a drive, snugly fit, and a niny little controller board). I'm looking for an upgrade because the filesystem on that drive bacame defective: it doesn't make more free space when you delete files, so I need another big-ish drive just to transfer all the data off it and reformat. If noone recommends any better, I'll look for USB3/SATA version of it.

---

