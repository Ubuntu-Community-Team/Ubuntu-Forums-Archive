---
title: "Hardware RAID1 working?"
date: 2009-10-10
forum: Hardware
---

### Post by reiti on 2009-10-10
hey!

I'm not experienced in using raid systems, but i want to setup an ubuntu server with a raid-1 system, it looks like this:

(excuse me it's german ;-) )

here is my fdisk -l output hoe somebody can help me!

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 K&#8730;&#8706;pfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 &#8730;ó 512 = 8225280 Bytes
Disk identifier: 0x0003ad13

   Ger&#8730;§t  boot.     Anfang        Ende     Bl&#8730;&#8706;cke   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Erweiterte
/dev/sda5           29165       30401     9936171   82  Linux Swap / Solaris

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 K&#8730;&#8706;pfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 &#8730;ó 512 = 8225280 Bytes
Disk identifier: 0x00000000

Festplatte /dev/sdb enthält keine gültige Partitionstabelle

Platte /dev/sdc: 500.1 GByte, 500107862016 Byte
255 K&#8730;&#8706;pfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 &#8730;ó 512 = 8225280 Bytes
Disk identifier: 0x00000000

Festplatte /dev/sdc enthält keine gültige Partitionstabelle

So accoring to the information promise gives me when i'm starting up the system raid 1 is running.
So i the 2 Drives sdb and adc should be the raid disks, does anybody know if that's correct??
and if the configuration is ok, which disk should i mount sdb or sdc??

thanks for help!!

greets

---

### Post by trundlenut on 2009-10-10
If it's hardware raid then unbuntu will only see the arrays not the individual disks.  What is physically in the box in terms of drives?  You shouldn't see 2 drives if the raid1 array is running.  You normally need to set up the arrays using the configuration tool which can be accessed during boot up.

One of my server has 5 drives set up with 2x32gb drives as raid1 and 3x72gb drives as raid5, Ubuntu just sees two discs, though I can't remember what it calls them off the top of my head.

---

### Post by superdav42 on 2009-10-10
Also do you know what raid controller you have? It's possible Linux does not support it yet.

---

### Post by reiti on 2009-10-11
I use a  promise Fasttrack TX 2300.

I have configured my raid 1 in the bootmenue correctly i think ( bootmenue says "RAID 1 Array functional")

I thought if the promise pci card makes a hardware raid i i don't need any linux drivers??

which raid hardware do you use??

---

### Post by trundlenut on 2009-10-11
how many drives do you have, from the code you posted it would appear there are 3 present but only one, sda, is partitioned.  If sdb and sdc are the drives attached to the raid controller and should be set up as raid 1 then something isn't working right.

---

### Post by reiti on 2009-10-11
sda is my Systemdisk where ubuntu is installed on and sdb and sdc are 500Gig disks which i want use with raid-1 as mirrored data disks, they are unformatted at the moment...

---

### Post by trundlenut on 2009-10-11
> **reiti said:**
> sda is my Systemdisk where ubuntu is installed on and sdb and sdc are 500Gig disks which i want use with raid-1 as mirrored data disks, they are unformatted at the moment...

Right so something is definately not working correctly.  You should see a single 500Gb disk and not two separate ones.  With hardware raid the OS should only see the arrays and not the individual disks.

Unfortunately I don't know anything about your specific raid controller, I should have a look on the manufacturers website and see if you can find more information on it.

---

### Post by superdav42 on 2009-10-14
I just looked it up according to [http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html") (look at the bottom) You got what is called a fakeraid device. It does not actually do any processing on its own but uses the cpu. And according to [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") Linux sees it as two independent disks. There is hope though as promise has released a partially binary driver for Linux 2.6 that you could compile and use. I might not be very easy but it use your hardware the way it was intended. Of course it would probably be easier just to use mdadm and setup software raid. If you are up for the challenge of compiling a kernel module you can get it here. [promise 2.6 linux partial source]("http://www.promise.com/support/download/download2_eng.asp?productID=136&category=all&os=100")

---

