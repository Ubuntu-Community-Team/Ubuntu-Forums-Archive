---
title: "Installing 8.10 with mirrored HD's"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by whaler1 on 2009-04-22
I just got a new Dell with mirrored 640GB SATA drives controlled by an Intel RAID. It came preloaded with VISTA which I want to dump in favor of Ubuntu. The system boots into Ubuntu fine from the CD but when I try and boot off the HD I get a "Try (hd0,0): EXT2:" message and then the system freezes. Any suggestions?

---

### Post by ronparent on 2009-04-22
Did you install from the desktop cd or the alternate install cd? From a live cd terminal post the output of 'sudo fsdisk -l'. Have you already partitioned and installed ubuntu - and with or without Vista?

---

### Post by whaler1 on 2009-04-22
Many thanks for the assistance,
 
I installed off the desktop download. I wiped Vista and did a basic HD format using Ubuntu's format tool. The following is the terminal output from the "sudo sfdisk -l" call.
 
ubuntu@ubuntu:~$ sudo sfdisk -l
 
Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
 
Device Boot Start End #cyls #blocks Id System
/dev/sda1 * 0+ 74843 74844- 601184398+ 83 Linux
/dev/sda2 74844 77824 2981 23944882+ 5 Extended
/dev/sda3 0 - 0 0 0 Empty
/dev/sda4 0 - 0 0 0 Empty
/dev/sda5 74844+ 77824 2981- 23944851 82 Linuxswap / Solaris
 
Disk /dev/sdb: 77825 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
 
Device Boot Start End #cyls #blocks Id System
/dev/sdb1 0 - 0 0 0 Empty
/dev/sdb2 0 - 0 0 0 Empty
/dev/sdb3 0 - 0 0 0 Empty
/dev/sdb4 0 - 0 0 0 Empty
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]
 
And one more thing, now when I try and boot the system from the HD I get the message;
No boot device available
SATA 0 : Installed
SATA 1 : Installed
SATA 2 : Installed
SATA 3 : None

---

### Post by whaler1 on 2009-04-23
Further information regarding the mirrored drive issue. 
 
I decided to try changing the HD control from RAID to ATA in the BIOS. Reinstalled 8.10 and the system boots fine after letting the installer partition the drive using the largest available space. Is there something I am missing WRT getting a RAID configuration to work with dual HDs. 
 
For anyone following this thread you have probably become aware that I have no history with LINUX....all I can say is that I am committed to figuring it out.

---

### Post by whaler1 on 2009-04-23
Use Alternate Installer....Doooh!

---

