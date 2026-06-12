---
title: "Ubuntu install problem on laptop"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by hurbie on 2009-06-08
Hi everyone!

I'm not good at computers so bear with me please. I don't have a complete description of the machine I have at hand but it is a Sony Vaio PCGFR25 which is a little bit old.  The total memory is 448 MB, it has pentium 4, a cd-dvd rom and I can boot from the cd. I had multiple problems with windows, especially with the blue screen telling me that there is a physical dump. Windows no longer worked since then (even during repair or re-install that blue screen will pop up). I got ubuntu 9.04 live cd and I'm trying to make it work.

The problem is that when I'm choosing the option "try ubuntu without any change to your computer", I get multiple problems and it doesn't want to work. I can't install ubuntu too. I've been successful loading the "try ubuntu without any change..."  only once (and it looks way better than windows!). But since then I haven't been able to make it work.

The problem is that when I choose option "try ubuntu..." I get those messages :
segmentation fault (core dumped)
/etc/unit.d/rc: 390: /etc/rc2.d/S86anacron: not found

If I select option like "nolapic", "acpi=off", "noapic", "edd=on" and the option "safe graphics mode", I get messages that say:
SQUASHFS error: unable to read page: block 3bd383; size 69a0 (the numbers vary as there 're plenty of error massages, pages and pages of them)
SQUASHFS error: unable to read fragment cache block 0xa62
['number'.'number'] BufferI/O error on device sr0, logical block 'number' ( 'number' designates some number)
BufferI/O error on device loop0, logical block # (# designates some number)

I should note that I get PLENTY of SQUASHFS errors (what do they mean?).

However when it start it loads some things  (loading kernel modules [OK], starting kernel log daemon [OK], starting system log daemon [OK] etc..)

In the end I get
['number'.'number'] Code: bad EIP value.
['number'.'number'] EIP [<401cd630>] 0x401cd630 SS:ESP 0068:d9a6be28
['number'.'number'] Kernel panic - not syncing: Fatal exeption in interrupt.

What can I do?

Thank you all for your help in advance!

---

### Post by 67GTA on 2009-06-08
Looks like a bad ISO image or bad burn. Did you check the MD5 sum of the ISO image? What did you use to burn it? Could also be bad RAM, DVD/CD drive, or hard drive.

---

### Post by Mueez on 2009-06-08
have you tried wubi?

---

### Post by yaroto98 on 2009-06-08
I agree, it's probably a bad image. You'll have check the md5 hash of the .iso you have, if it's correct - reburn it, but if it's wrong - you'll have to redownload it all and then burn it.

---

### Post by hurbie on 2009-06-08
> **67GTA said:**
> Looks like a bad ISO image or bad burn. Did you check the MD5 sum of the ISO image? What did you use to burn it? Could also be bad RAM, DVD/CD drive, or hard drive.

Hi 67GTA, 

yes, I checked the MD5sum of the ISO image and it's OK.
I used ImgBurn to do the cd. I'm going to try to burn it at the slowest speed.
Could be a bad RAM: the RAM has a LOT of errors when I run memtest86+.

---

### Post by hurbie on 2009-06-08
> **Mueez said:**
> have you tried wubi?

Hi Mueez,
Can one try wubi without windows or even if windows doesn't work?

---

### Post by hurbie on 2009-06-08
Considering that the problem is maybe due to bad RAM, is there any way to avoid this bad RAM problem? Will using an older version of Ubuntu help?

Does updating the Bios help? I would like to update the bios of the machine but there's no OS working on it: windows seems badly broken, it can't work at all, under no conditions and i can't install Ubuntu. I've only been successful using the "try Ubuntu" option only once. Can a bios be updated with a cd during the boot?

Thx!

---

### Post by 67GTA on 2009-06-08
> **hurbie said:**
> Hi 67GTA, 

yes, I checked the MD5sum of the ISO image and it's OK.
I used ImgBurn to do the cd. I'm going to try to burn it at the slowest speed.
Could be a bad RAM: the RAM has a LOT of errors when I run memtest86+.

That's your trouble. You need to replace the RAM. Wubi is only for installation from inside Windows. It creates a virtual Ubuntu in your Windows filesystem.

---

### Post by 67GTA on 2009-06-08
RAM (random access memory) is a vital part of your computer. You can't run any OS reliably with bad RAM.

---

