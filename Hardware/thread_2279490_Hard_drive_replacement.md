---
title: "Hard drive replacement"
date: 2015-05-23
forum: Hardware
---

### Post by AlyssaVS on 2015-05-23
I have a Sony Vaio that I bought refurbed in 2012. The hard drive is failing. Was looking for the HDD specific to the laptop model but noticed that it's a Toshiba drive placed probably when it was refurbed. I have everything I need backed up. I also have the Windows recovery disk and of course the usb flash drive to reinstall ubuntu. 

My question is, assuming the drive is of equal size or greater (which it will be) do I need to buy the same exact HDD to replace it? Or is that only if I was planning to reinstall everything from a cloned system? I became confused when considering drivers and other software specific to the system. Since it isn't a Sony HDD, what issues would I face if I replaced it with a Sony? I run a dual partition with Windows 7 and Ubuntu 14.10 and am pretty comfortable setting that up again after installing the new drive.

My system:
Sony Vaio VPCEG 37FM
5 GiB
intel core i5-2450M CPU @ 2.50 GHZ x4
32-bit
272.2 GB

Any help/advice would be greatly appreciated. :)

---

### Post by weatherman2 on 2015-05-23
Hard drives are pretty generic in laptops, beyond some basic specs.  No, you most certainly don't need to put the same type or size in - many of us upgrade the drives in our laptops even when the drives aren't failing. That Toshiba drive may have been the original drive.  Sony doesn't make hard drives to my knowledge but Toshiba does.  One of my Acer netbooks came with a Toshiba drive as the original drive, too.

Your Sony probably takes a 2.5" SATA laptop drive (it could also be the smaller 1.8" size - you should confirm this).  The 2.5" drive size could also be a 9.5mm thickness or only 7mm thick.  If original drive is is 9.5mm, you can replace it with another 9.5mm drive or with a 7mm drive (and a spacer, which may come with the drive, to make it fit 9.5mm), but you probably can't use a 9.5mm drive to replace a 7mm original drive.  To confirm the real size without actually opening the thing up yet, find the exact model of Toshiba drive and google the specs.  You should be able to get this info in various ways in Linux.  One way is to open a terminal (assuming the drive still works at least somewhat) and type the command "sudo lshw") and find the drive model number somewhere in the results.

If your original drive is only starting to fail, you might have luck cloning it to a new drive of the same size or larger, if you want to.  I have done that many times.  Clonezilla (booted from say a USB flash drive) will probably do it quickly, but you'll either need a USB hard drive enclosure (to attach both drives at the same time, so you can copy/clone from one to the other) or an external/portable USB drive (with a lot of free space) so you can do the clone in two steps: copy/clone the original drive to a big image on the USB drive, then swap in your replacement drive and restore the image you just made to the new drive.  Or you can forget all of that and just start over and re-install both Windows and Ubuntu from scratch, if you want.

Personally, unless you can't afford it, these days I would upgrade to an SSD drive instead of another hard drive.  SSD prices have come way down in recent years, and an SSD will make your laptop run a lot faster and maybe make it last a few more years.

---

### Post by AlyssaVS on 2015-05-23
> **weatherman2 said:**
> Hard drives are pretty generic in laptops, beyond some basic specs.  No, you most certainly don't need to put the same type or size in - many of us upgrade the drives in our laptops even when the drives aren't failing. That Toshiba drive may have been the original drive.  Sony doesn't make hard drives to my knowledge but Toshiba does.  One of my Acer netbooks came with a Toshiba drive as the original drive, too.

Your Sony probably takes a 2.5" SATA laptop drive (it could also be the smaller 1.8" size - you should confirm this).  The 2.5" drive size could also be a 9.5mm thickness or only 7mm thick.  If original drive is is 9.5mm, you can replace it with another 9.5mm drive or with a 7mm drive (and a spacer, which may come with the drive, to make it fit 9.5mm), but you probably can't use a 9.5mm drive to replace a 7mm original drive.  To confirm the real size without actually opening the thing up yet, find the exact model of Toshiba drive and google the specs.  You should be able to get this info in various ways in Linux.  One way is to open a terminal (assuming the drive still works at least somewhat) and type the command "sudo lshw") and find the drive model number somewhere in the results.

If your original drive is only starting to fail, you might have luck cloning it to a new drive of the same size or larger, if you want to.  I have done that many times.  Clonezilla (booted from say a USB flash drive) will probably do it quickly, but you'll either need a USB hard drive enclosure (to attach both drives at the same time, so you can copy/clone from one to the other) or an external/portable USB drive (with a lot of free space) so you can do the clone in two steps: copy/clone the original drive to a big image on the USB drive, then swap in your replacement drive and restore the image you just made to the new drive.  Or you can forget all of that and just start over and re-install both Windows and Ubuntu from scratch, if you want.

Personally, unless you can't afford it, these days I would upgrade to an SSD drive instead of another hard drive.  SSD prices have come way down in recent years, and an SSD will make your laptop run a lot faster and maybe make it last a few more years.

Thank you so much for the answer. This really helps. The drive has been failing and it is almost toast , I had clonezilla ready to go but it's too late (got lazy from work and procrastinated). I would rather do an SSD but had heard the average price is almost a dollar per gigabyte. If it's closer in price to the HDD than before then sweet. But I gotta go as cheap as possible since I also need to buy a new battery (thanks to my laziness I let that go too long... hello failed hard drive :( ). I will do more research and maybe I'll get lucky. I feel a lot better about doing the replacement thanks to your help! Enjoy your weekend. :)

---

### Post by weatherman2 on 2015-05-23
I have seen 500GB (or 512GB) SSD drives on sale for under $200 USD, sometimes well under $200 - I paid almost 50% more than that a year ago.  As I said, that would give you a nice speed boost too.  Check prices of all kinds of drives.  The cost difference might not be as much as you think.

You might find a cheap replacement battery on eBay, but I imagine Sony batteries are more expensive than other brands.  Good luck!

---

