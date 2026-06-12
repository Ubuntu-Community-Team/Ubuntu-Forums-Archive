---
title: "initird-tools fails to install on new installation"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by Kaustav on 2006-02-03
Update
I've just done a CD verify and it seems some of the files on my Ubuntu installation CD failed CRC check. Maybe that's the cause of my installation problems. I'm downloading the ISO again and burning a new install CD..


I've started to install Ubuntu on an old PC that runs Windows 2000. 160GB HD with 80GB free unallocated unpartitioned disk space for Ubuntu.  I proceed to installation and manually set up my paritions using the Ubuntu installer. This is my set up:

[FONT=Courier New]
Device         Boot  Start     End         Block              ID    System
/dev/hda1              8               11103   83885728+   7      HPFS/NTFS
/dev/hda2              11104     20473   70837200     83    Linux
/dev/hda3  *    1                7             52888+          83    Linux
/dev/hda4      20474     20673   1512000        82    Linux swap / Solaris
[/FONT]

I used Parition Magic to move my NTFS partition up so I had approx 50Mb free at the start of the disk to boot the /boot partition on. 

Installation fail whilst installing the base system and the error is:

An error was returned while tyring to install the initrd-tools package onto target system. Check /target/var/log/bootstrap.log for details.  

When I go in to that directory there is no bootstrap.log file there!  

I'm using Phoenix Bios 4 6.0.E, Version: HY.01.05US. The machine is a P3, 800MHz system with 512Mb RAM. 

Does anyone know what's wrong with this? I also tried an install without the 50Mb /boot partition. i.e. I just deleted that partition and did not format it. I just created the automatic patitions, i.e. /swap and /    I also ensured that / was bootable.

---

### Post by az on 2006-02-03
[QUOTE=Kaustav]Update
I've just done a CD verify and it seems some of the files on my Ubuntu installation CD failed CRC check. Maybe that's the cause of my installation problems. I'm downloading the ISO again and burning a new install CD..
...
An error was returned while tyring to install the initrd-tools package onto target system. Check /target/var/log/bootstrap.log for details.  
[/QUOTE]
There is no other reason for that error than a corrupt cd.  It is telling you that it cannot copy it from the cd to your drive.

---

### Post by pnael on 2006-02-06
It seems that if you burn a install CD (for me a CD-RW)  with a speed > 10 you get this error. Burning again the same iso, using the same options but with a speed <= 10 solved the problem. I don't know why ???

---

