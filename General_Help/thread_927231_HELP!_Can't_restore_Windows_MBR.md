---
title: "HELP! Can't restore Windows MBR"
date: 2008-09-22
forum: General Help
---

### Post by Crazyap7 on 2008-09-22
Hello, I'm currently dual-booting Ubuntu Gutsy Gibbon and Windows XP SP3 on my pc. My Linux was installed on a 4GB flash drive, so I need to plug in my flash drive so that Ubuntu can load GRUB and I can choose to boot to Ubuntu or Windows. So anyways that works fine but now I want to remove the dual-boot and restore the Windows MBR. 
How would I go around doing this???? So far I've reinstalled Windows on my C: partition (system files, boot loader etc.) but I haven't touched my D: partition which is where My Documents is located. When that didn't work and I still needed GRUB to boot, I attempted to flash my BIOS and see if that work. I now have the latest BIOS but I still need GRUB to load. Then I tried booting into my Windows recovery console from the disk and type FIXMBR into the console, but unfortunately while the disk was loading the files needed to load the recovery console it blue screened and made me restart. I've tried booting into the disk several times and it still blue screens each time. Where has Ubuntu put GRUB????? ZOMG I need it off or I'm going to explode! Not really but please please post if you have any idea on how to fix my problem. 

*PS: My windows recovery disk was from SP2, not SP3, but I don't see how that would make a difference. If the SP3 disk is actually needed instead of SP2 since I have SP3 installed on my pc, please say so.

---

### Post by cariboo on 2008-09-22
Seeing as you don't have a proper windows xp installation cd you may want to go here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and download the iso. Super Grub Disk has the files needed to repair your mbr.

If you have access to a windows installation cd boot into the recovery console and use FIXMBR and FIXBOOT to repair your mbr.

Jim

---

### Post by Crazyap7 on 2008-09-22
Ok thank you, I'll try that and give an update in the next few days.

---

