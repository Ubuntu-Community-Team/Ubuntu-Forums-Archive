---
title: "Grub Error 18 after successful install"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by diamondjim08 on 2009-08-18
After successfully installing Ubuntu 9.04 on a Dell E1705 notebook and running it for a week, I tried to boot the old XP hard drive via the USB port.  I changed the boot sequence in the BIOS setup to boot from USB first and then the Hard drive with Ubuntu.
My installation of Ubuntu ran perfectly before attempting to boot XP from the old drive.  When XP tried to boot from the USB port, the XP splash screen came up and then all hell broke loose - blue screens with warnings and dire consequences to follow.  So I changed the boot sequence back to Ubuntu (now the internal HD) and got "Grub loading...error 18".
Can I recover from this by editing the Grub file or is this installation trashed?  Like I said, this install worked perfectly until I did this.
Any help or suggestions? 
Many Thanks,
<>Jim

---

### Post by VMC on 2009-08-18
Here's stage2 error 18 explained:
 Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

You might want to re-check your BIOS settings. Make sure their correct.

Here's another [LINK]("http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html") on same error.

---

### Post by diamondjim08 on 2009-08-18
Hi VMC,
Thanks for the message.  
What does this have to do with me trying to boot the old HD (120g) from from the USB?  Did Windoz write something to the MBR on the new 250g drive (Ubuntu) and produce this error?  Is GRUB confused about which drive to boot expecting something else?
The BIOS in the Dell E1705 is easy to get into but it does not say much about the hard drive specs.
I'm not sure I understand your answer enough and how it relates to what I did so I can fix it.  Can you give me more details at my level?
Thanks,
<> Jim

---

### Post by raymondh on 2009-08-18
Here's [Herman's take on error 18]("http://members.iinet.net.au/~herman546/p15.html#18").  Noteworthy (if you scroll down) is his comment about the cables.  Hope this helps.

EDIT : after re-reading your first post, I realized you don't have a master/slave 2 HD set-up.  You might want to consider either a /boot partition or moving Ubuntu closer.  Did you update kernels just before error 18 came on?

---

### Post by diamondjim08 on 2009-08-19
Thanks for all the replies!  Here is what I have done since last night:
I used Super Grub Disk to try and recover... no luck.  After trying the simple stuff - bios settings, SGD and the like, I decided to wipe the disk and reinstall.  Everything went well until I tried the reboot... Error 18 again! :-(  I replaced the 250 GB SATA drive with a new 250 GB SATA and installed again.  Perfect.  Everything went as designed.
The old 250 was placed in a USB case to try and find out what could be done to fix the drive.  
Itried to read it using my MAC Disk Utility and this is what it reported: 110.4 GB WDC WD25; disk2s1.  So there are two disks with only 100.4 GB, half the size of what it is supposed to be!
How can I recover the rest of the drive space?
Thanks,
<> Jim

---

### Post by diamondjim08 on 2009-08-19
here is the partition table message:
ubuntu@ubuntu:~$ dmesg | tail
[ 1066.458422] attempt to access beyond end of device
[ 1066.458425] sdc: rw=0, want=476375445, limit=231496650
[ 1066.534321] attempt to access beyond end of device
[ 1066.534330] sdc: rw=0, want=476375447, limit=231496650
[ 1066.534338] attempt to access beyond end of device
[ 1066.534342] sdc: rw=0, want=476375447, limit=231496650
[ 1066.754564] attempt to access beyond end of device
[ 1066.754575] sdc: rw=0, want=237768791, limit=231496650
[ 1066.754579] JBD: IO error reading journal superblock
[ 1066.754584] EXT3-fs: error loading journal.

---

