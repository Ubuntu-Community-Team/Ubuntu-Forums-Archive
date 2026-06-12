---
title: "SATA drive not read"
date: 2009-09-06
forum: Hardware
---

### Post by samrobb1 on 2009-09-06
Hey, I have two computers; a windows machine and a laptop with jaunty installed
A few nights ago I was using my laptop and my windows desktop restarted itself, so I checked why and the hard drive stopped working. I've tried everything I can think of to get this hard drive back on. I've even tried to see if I can use an ubuntu live cd to atleast access the files on it but no luck.

I've opened up my computer and taken the drive out, and I can hear that it is turned on when the computer is turned on (I can hear the hard disk spinning) which makes me wonder if it's the motherboard, but everything else loads, ie. BiOS, monitors, mouse, keyboard, etc but not the hard drive.

So is there anything that can be done to get it back working or do I need to buy a new hard drive? Also is there any sort of program on the ubuntu live cd for me to check the drive?

Hard Drive Specs: Seagate Barracuda, 7200RPM, 500GB, model no. ST3500320AS

---

### Post by lindsay7 on 2009-09-06
I would download "Testdisk" and run it on your drive and see what you get.  Testdisk is free.

You could also us the live cd to run Gparted and see if it sees your drive and what is on it.

---

### Post by samrobb1 on 2009-09-07
I checked for the drive with GParted on the live CD and nothing showed up

---

### Post by lindsay7 on 2009-09-07
Here is the info on the Testdisk site,

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


You could download the Linux version to a usb drive and run it from the live cd. Testdisk is in the Ubuntu programs that can be installed using the add/remove option or the Synaptic Package manager.

---

### Post by queenxalik7 on 2011-01-15
> **samrobb1 said:**
> Hey, I have two computers; a windows machine and a laptop with jaunty installedA few nights ago I was using my laptop and my windows desktop restarted itself, so I checked why and the hard drive stopped working. I've tried everything I can think of to get this hard drive back on. I've even tried to see if I can use an ubuntu live cd to atleast access the files on it but no luck.I've opened up my computer and taken the drive out, and I can hear that it is [[COLOR=#000000]turned[/COLOR]](http://www.itposts.net/id/software/export-ppt-to-pdf-with-any-application-it-is.html) on when the computer is turned on (I can hear the hard disk spinning) which makes me wonder if it's the motherboard, but everything else loads, ie. BiOS, monitors, mouse, keyboard, etc but not the hard drive.So is there anything that can be done to get it back working or do I need to buy a new hard drive? Also is there any sort of program on the ubuntu live cd for me to check the drive?Hard Drive Specs: Seagate Barracuda, 7200RPM, 500GB, model no. ST3500320ASSomething error occurs when opening the link, Is the link invalid?

---

### Post by gordintoronto on 2011-01-15
If it's not the SATA cable, it's probably the drive.

Are there other SATA ports on the motherboard?

---

