---
title: "Botched 9.10 installation killed my SSDD!"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Qwertinsky on 2009-11-08
I tried installing Ubuntu 9.10 on my Asus EeePC netbook this morning.

Everything was going along fine up until about 95% when the grub installation crashed.

This left my main SSDD (solid state disk drive) in a state that is can not be read or written to.

To top it off this SSDD is soldered in and replacement would be a real P.I.T.A.

Further installation attempts the partitioner in graphical installers return an I/O error, and text based installers just say "operation failed" when trying to do anything to this drive.

Gparted scans it then seems to ignore it as sdb (second drive) and sdc (usb drive) show up as devices but not sda?

When running a Windows XP installer, it sees the drive but says "Windows can not access this device"

This all kind of leads me to believe the drive is somehow locked.

Anyone recommend something that could fix this that also can be booted from a USB device?

---

### Post by Full_Auto_Legos on 2009-11-08
Wow.  Sounds Bad.  I'm not sure it will be any better than GParted, but you could try DBAN :  [www.dban.org](www.dban.org)

---

### Post by Togezo on 2009-11-08
Oddly enough, I have encountered this problem twice while patrolling these forums, and both times with an eee PC

The other thread is here:
[http://ubuntuforums.org/showthread.php?t=1318338](http://ubuntuforums.org/showthread.php?t=1318338)

---

### Post by Qwertinsky on 2009-11-08
I fixed it by low level formatting the drive using

HDD Low Level Format Tool from HDDGURU.COM

[http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/](http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/)

You have to be able to boot to Windows to use this. I was lucky and still could boot my Windows partition from a USB drive.

I have seen places on the net with instruction on how to install Windows XP to a flash dive in a way that makes it bootable and usable.

I am back to 9.04 and holding.

---

