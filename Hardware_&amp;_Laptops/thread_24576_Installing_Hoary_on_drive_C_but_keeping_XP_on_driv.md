---
title: "Installing Hoary on drive C: but keeping XP on drive D: intact - Possible?"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Leigh on 2005-04-07
My work PC is a Windows XP box with 2 hard drives installed. Drive C is Windows 2000, drive D is XP. Currently I can dual boot between either OS.

What I want to do is install Ubuntu on the drive C, wiping out Windows 2000 (as I don't use it anymore) but the D drive, containing XP, must remain intact. 

So my question is after having installed Ubuntu on drive C, does it have some sort of boot manager that will let me boot to XP should I need to?

(I can't imagine that this is particularly difficult to do as i have two separate drives, most of the threads I've read about dual booting are usually one drive with two partitions.)

Also, when I start the installation, how do I know which drive I will be install Hoary on? I don't want to accidentally wipe out XP. I know Linux naming conventions are different to Windows, so some advice here would be appreciated.

(You would be correct in assuming total Linux knowledge is zero.)

---

### Post by BeZet on 2005-04-07
First, you need to know, that you can't install any Linux distribution on 'C' or 'D' or other Windows partition (which uses FAT32 or FAT16 filesystem). Linux uses the ext2 file system, which you can't see in Windows.
But of course, it is possible to have Windows and LInux on one machine.

---

### Post by Leigh on 2005-04-07
Having a different filesystem will be no problem. When either OS is booted I won't need to see the other partition.

Ultimately, I want to use Linux as my everyday OS but I must be able to do everything I do now through Windows. I work in a support role so MUST have access to the network, servers, Internet, etc. I'd just rather do it through Linux from now on.

---

