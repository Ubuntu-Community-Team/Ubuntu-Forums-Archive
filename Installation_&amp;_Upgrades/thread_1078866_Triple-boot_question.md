---
title: "Triple-boot question"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by tedrow on 2009-02-23
2-month old Dell D630 laptop, 4GB mem, nVidia graphics.

Lots of multi-boot info here in the forums, but I don't see quite what I'm looking for (although I may have missed it in the 2+ hours I scanned the forums...)

Central IT loaded my laptop with XP-Pro and a boatload of applications, per corp standard.  I had the IT guys partition the disk 3 ways, so C:\=XP-Pro (only), D:\=mydata, and E:\ =Ubuntu 8.04.2 (2.6.24-23) in an ext3 partition with no swap.  Ubuntu was installed (by me, downloaded image) from boot-to-CD, like a snap with no problems, and I edited the grub file to allow unattended re-boot to default to XP. Everything is stable and A-OK.

Now (arrggghh) I need to test some apps under Vista. I have the Dell OEM disk to load it.  Trashing and re-doing Ubuntu would not be painful, if it simplifies my goal, but re-doing XP would be *very* painful because of the significant apps-reload hassle.  So, I want to keep XP stable whatever else I do.  Backing up D:\*mydata* is also not difficult.

I found the 4-part vid to tri-boot XP, Vista and Ubuntu, and that tells me it'll work - but he started from blank disks and I already have XP and then loaded Ubuntu so grub is handing the boot process.  Partition space is not an issue, but I do not plan to add any more partitions to accommodate Vista.

If I merely install Vista to D:\ without any other preps, will the boot-manager be hosed?  (I believe yes, and that after the the Vista load, I'll see Vista and XP but no Ubuntu.) If so and I re-load Ubuntu after Vista, will it recover such that grub will manage all three OS'es?  I'd prefer that an unattended boot defaults to XP after I'm done... All the partitions are on the same hard-drive, so I don't worry much about where the boot-loader is managed from -- if the drive blows out - it takes everything and I start over anyway.

So - is there an optimal way to approach this, or is it as simple as loading Vista as the machine sits?  Many thanks in advance - I appreciate your time to help me before I do something destabilizing.

---

### Post by cariboo on 2009-02-23
Wouldn't be easier to run it in a vm. Virtualbox is in the repeositories and you can install it using synaptic. I currently have xp, vista and windows 7 in vm's. If you intend on loading 64bit Vista or need usb, you will have to get the deb from [Virtualbox]("http://www.virtualbox.org/") as the version in the repositories will not do usb or 64bit networking.

Jim

---

### Post by caljohnsmith on 2009-02-23
If you want to install Vista to that HDD, I think the biggest question is what type of OEM Vista Install CD do you have? If it is not a genuine Windows Install CD (which I assume it isn't since you said it was OEM), then chances are your Dell OEM CD will completely erase the HDD and install Vista from scratch. That's usually the way OEM Install CDs work unfortunately. But if you can somehow get a Vista Install CD that will install Vista just to a partition, you should be fine. It is easy to reinstall Grub afterwards, there is definitely no need to reinstall Ubuntu (assuming the Ubuntu partition is left untouched by the Vista installler).

---

