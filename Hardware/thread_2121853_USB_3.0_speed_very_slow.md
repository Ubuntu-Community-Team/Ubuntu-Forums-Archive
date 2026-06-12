---
title: "USB 3.0 speed very slow?"
date: 2013-03-03
forum: Hardware
---

### Post by Shin Asuka on 2013-03-03
Yesterday I got this Toshiba HDTB115EK3BA 1,5TB external drive
plugged it into my  
AMD A6-3670 / Asus f1 m75 HTPC / xubuntu 12.10
problem is, I only get 25mb/s write speed.

Based on the amazon reviews it can do 70mb/s on a usb3 connection.

I notice kinda high cpu load, don't know if this could be the issue.

[ATTACH]239699[/ATTACH]
[ATTACH]239700[/ATTACH]
[ATTACH]239701[/ATTACH]

Anyone got an idea?

EDIT: just tried it on a Windows 7 laptop and got 91mb/s ... wtf?
will try bios update next but..

---

### Post by Shin Asuka on 2013-03-03
Bios Updated from 2201 to 2206

no change... stil 25mb/s :(

(shameless bump)

---

### Post by MikeBraxner on 2013-03-05
Sounds like your using an NTFS pre-formated drive. While the NTFS drivers used allow you to read and write without problems, the resulting speed can be a drag. Unless you're dependent on NTFS, I would suggest trying a native format, say ext4, that should relieve the speed issue at least to some degree.

---

### Post by Mark Phelps on 2013-03-05
From my knowledge, Ubuntu 12.10 comes with current NTFS drivers built-in.  I use 12.10 with USB 3 drives and don't notice any performance degradation over using Win7 with the same drives.

Notice you did a BIOS upgrade -- but in your first post, you said that you already got acceptable USB3 speeds in Win7 -- which, by definition, would use the SAME BIOS version -- since that is entirely OS independent.  Curious about what inspired you to do a BIOS upgrade.

I did have a USB3 performance problem when I first assembled this machine, but that was fixed using a firmware upgrade to the USB 3.0 chip on the motherboard, not to the BIOS.  Unfortunately, I had to do that upgrade in Windows.

---

### Post by Shin Asuka on 2013-03-05
> **Mark Phelps said:**
> From my knowledge, Ubuntu 12.10 comes with current NTFS drivers built-in.  I use 12.10 with USB 3 drives and don't notice any performance degradation over using Win7 with the same drives.

Notice you did a BIOS upgrade -- but in your first post, you said that you already got acceptable USB3 speeds in Win7 -- which, by definition, would use the SAME BIOS version -- since that is entirely OS independent.  Curious about what inspired you to do a BIOS upgrade.

I did have a USB3 performance problem when I first assembled this machine, but that was fixed using a firmware upgrade to the USB 3.0 chip on the motherboard, not to the BIOS.  Unfortunately, I had to do that upgrade in Windows.

No, as I said, I tried a Laptop (some ACER intel i5m) with USB 3 and got 91mb/s.

My AMD HTPC only has Ubuntu on an SSD, I would like to try with Windows here but... don't want to reformat everything :/

Why I did a BIOS Update (that didn't help)? Well just try to get this damn thing working, can't hurt, can it?

Also the external drive is for regulary copying files to a windows box, so unless you have a good ext4 windows7 driver that is no option ;)

---

### Post by justincarter on 2013-03-06
see the device manager and bios settings.

---

### Post by Shin Asuka on 2013-03-06
> **justincarter said:**
> see the device manager and bios settings.

sorry, what?

---

### Post by Mark Phelps on 2013-03-06
> **Shin Asuka said:**
> .. Why I did a BIOS Update (that didn't help)? Well just try to get this damn thing working, can't hurt, can it?

Actually, for future reference -- YES, it can!

I used to think along the same lines, until one day, I did a routine BIOS update to my Gigabyte motherboard and afterward it would not boot to the OS.

Did the usual stuff about removing the battery, choosing defaults, etc. -- nothing helped.

Fortunately, I did what many folks do NOT do -- I did a backup of my working BIOS before I flashed the update.  So, I was able to reflash back to the working BIOS version -- and all was OK again.  Later, Gigabytye removed that BIOS upgrade from their website.

So, yes, a bad BIOS update can trash your PC -- so don't just do it hoping it will fix something.

---

### Post by Mark Phelps on 2013-03-06
> **Shin Asuka said:**
> sorry, what?

As you noticed, vague suggestions like this one are not much use ...

Especially, as there is no actual Device Manager in Ubuntu -- but instead, there is HWInfo. That would give you information about the USB 3.0 in your PC -- which could be useful for you to track down firmware updates.

As to the BIOS settings, you could check to see if there is an option to enable/disable USB 3.0 -- but, it should be enabled by default.

---

### Post by Shin Asuka on 2013-03-06
> **Mark Phelps said:**
> As you noticed, vague suggestions like this one are not much use ...

Don't you say...
 if I should clarify anything, please tell me.

> **Mark Phelps said:**
> 
Especially, as there is no actual Device Manager in Ubuntu -- but instead, there is HWInfo. That would give you information about the USB 3.0 in your PC -- which could be useful for you to track down firmware updates.

Wait, first you tell me not to do BIOS updates, now you tell me to look for firmware updates?

> **Mark Phelps said:**
> 
As to the BIOS settings, you could check to see if there is an option to enable/disable USB 3.0 -- but, it should be enabled by default.
there is no such option.

---

### Post by sudodus on 2013-03-06
> **MikeBraxner said:**
> Sounds like your using an NTFS pre-formated drive. While the NTFS drivers used allow you to read and write without problems, the resulting speed can be a drag. Unless you're dependent on NTFS, I would suggest trying a native format, say ext4, that should relieve the speed issue at least to some degree.
+1

I think it is worthwhile to check a little along this track. If you have (or can get) a USB 3 pendrive, you can test it with different file systems, ext2, ext4, FAT32, NTFS. I can almost ;-) bet that NTFS will be way slower than the other file systems when connected from linux.

Would you be prepared to test ext4 with this driver in Windows? (It can also be evaluated with a USB 3 pendrive).
[[COLOR=#ff0000]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by justincarter on 2013-03-12
**Thanks for sharing. Nice information.**

---

### Post by justincarter on 2013-03-12
Mark Phelps you are right. Thanks for explaining on my behalf .

---

### Post by kurt18947 on 2013-03-12
I think there is also an issue that not all USB 3 chipsets on motherboards perform equally well with linux drivers.  Some are better than others and except for adding a PCIe card, there is not a practical way to change or upgrade.  It seems that USB 3 is still maturing, at least on Linux.

---

