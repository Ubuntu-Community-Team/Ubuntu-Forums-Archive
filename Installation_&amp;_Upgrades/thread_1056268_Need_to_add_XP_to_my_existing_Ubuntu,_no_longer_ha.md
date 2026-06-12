---
title: "Need to add XP to my existing Ubuntu, no longer have Ubuntu disc. Possible?"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by EvilBear on 2009-01-31
Need to add XP to my existing Ubuntu, no longer have Ubuntu disc. Is it possible to do that somehow, or do i need to request another disc? If it is possible...how? Need it for classes starting in 2 days. I have a dell laptop with ubuntu unstalled. Help?


All i need xp for is for school, to run visual basic.net. I am to noobish to use mono, so need to dual boot. Also need to be able to use itunes for this damned iphone. Those are the only 2 requirements for this dual boot.

---

### Post by directhex on 2009-01-31
Life would be much easier if you could boot Ubuntu from removable media - the XP installer will remove your ability to boot non-Windows systems

You don't have a blank CD? or a USB drive?

---

### Post by ajgreeny on 2009-01-31
If you don't want to download a big ubuntu.iso file, get any other small live CD of a linux distro (eg puppy) or download supergrub and you will be able to use that to restore grub after you have reinstalled windows.  You will then need to add the grub entry for windows to the grub menu.lst file manually, but it should be easy enough to do.

You might also be able to do it with the ubuntu minimal iso from [here]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso").

---

### Post by EvilBear on 2009-01-31
The other media I have are a SD card that can hold 1gb and a portable HD that uses the USB port, that holds 500gbs. Any way to us one of those?

---

### Post by EvilBear on 2009-01-31
> **ajgreeny said:**
> If you don't want to download a big ubuntu.iso file, get any other small live CD of a linux distro (eg puppy) or download supergrub and you will be able to use that to restore grub after you have reinstalled windows.  You will then need to add the grub entry for windows to the grub menu.lst file manually, but it should be easy enough to do.

You might also be able to do it with the ubuntu minimal iso from [here]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso").

Willing to do whatever works and keeps my Ubuntu intact, all files, preferences unchanged. Still new to ubuntu though, so would need help implementing that. I know how to open a terminal and follow directions, pls a little of vim. :)

---

### Post by EvilBear on 2009-01-31
Ok, found a stash of blank CD's as well. Steps for using those possibly?

---

### Post by MarblePanther on 2009-01-31
Burn supergrubdisk to a cd.  The link is in my sig.  --download the CDROM image

After you burn it, restart and boot your supergrubdisk cd to restore GRUB after windows has wiped it.

---

### Post by EvilBear on 2009-01-31
Someone i know just told me about something called patition magic and that if i use that i wouldn't need to reinstall the grub. i know that partitioning makes hd space seperate, but thats alli know.

---

### Post by directhex on 2009-01-31
> **EvilBear said:**
> Someone i know just told me about something called patition magic and that if i use that i wouldn't need to reinstall the grub. i know that partitioning makes hd space seperate, but thats alli know.

Your associate is wrong, and confusing two issues

Issue 1: you need an empty partition to install XP onto. If you try and use the XP installer to repartition, it will erase all your data. Use a Linux live-cd (e.g. an Ubuntu CD) to repartition your existing Ubuntu partition to be smaller and leave empty space for XP to use as a partition - or boot a Partition Magic CD instead

Issue 2: Distinct from the partition question is the "boot sector". This is the first area on your hard disk, and is used by the BIOS to start loading an operating system. No matter what you do, XP's installer will delete your current boot sector & install its own (which will just boot XP). You need to re-install the Grub boot sector afterwards, which will allow you to pick between different OSes. This can be done with a live-cd (e.g. an Ubuntu CD) but not by something like Partition Magic

---

### Post by EvilBear on 2009-01-31
Thank you. For safety's sake, since i found out i do not need my .net till next saturday, I will be bringing my laptop to the schools computer building and having the resident Linux Guru help me follow these instructions. Also, i need to wait till i get a copy of XP, which i shall be getting for free because of the class I am taking. Thank you for the help. If i still can't get it to work after monday evening, i'll be back here, but with an ubuntu disc. 

Adam

---

