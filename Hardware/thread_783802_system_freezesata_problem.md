---
title: "system freezes/ata problem"
date: 2008-05-06
forum: Hardware
---

### Post by ajeje on 2008-05-06
Dear all,
I recently updated my laptop running ubuntu 7.04 to hardy.
The laptop is a Toshiba Satellite M40, 2Gb RAM.
Since very little space was left on the hard disk, I replaced the one I had (Hitachi, 80 Gb), with a new one (Samsung, 120 Gb). I have a dual boot system, running Xp and Ubuntu, with 4 partitions (1 ntfs, 3 ext3) and swap.
I mirrored all the partitions from the old to the new disk, reformatted /boot and /, and installed Hardy. Installation finished smoothly and quickly. Windows XP works fine. However, since the very first boot, I had a problem with Ubuntu. The boot works fine, does not  hang and is fast. But after a few minutes the system freezes for a few seconds (10/20 sec), then recovers. The mouse and the screen still work, as well as vlc listening some music).
The problem seems related to the disk controller (ata/pata), since I get an error in the dmesg (ata port is slow to respond, please be patient). Actually, I am no more patient, since the freezes occur every 3/4 minutes! ](*,) Impossible to work on such machine.

The disk is new. SMART tools show that it is healthy, and I also run the diagnostic tool from samsung. No problems found on the device. The  controller seems ok, since works fine with Windows and Feisty.

I googled for the problem, and seems that a lot of people got the same error. However, I can not find a clear explanation and answer. Someone claims it is a conflict with the CD/DVD. I updated the bios and removed the DVD from the machine, but the problem persists. Others claim it is a problem of a buggy driver. I loaded some alternative driver, and blacklisted the buggy one. No improvements. Tried to pass the option 'libata.atapi_enabled=1' to the kernel at boot time. No success. At one point I also managed to configure the hard disk as IDE (/dev/hda). I did not get rid of the freezes, but got some different errors on dmesg. I spent almost 2 days, and really need to get some work done. Now I am back to the old disk, running Ubuntu 7.04.

Any clue on this? 
Thanks to everybody

Ale
PS the kernel was the one shipped with the ubuntu cd (2.6.24-16-generic?).

---

