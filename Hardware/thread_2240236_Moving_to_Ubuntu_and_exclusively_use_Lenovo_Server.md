---
title: "Moving to Ubuntu and exclusively use Lenovo Servers"
date: 2014-08-18
forum: Hardware
---

### Post by t-andruw-b on 2014-08-18
We will soon begin to deploy system with Ubuntu, and will exclusively use Lenovo Server Equipment.
The current Hardware lists includes only systems that have been discontinued by Lenovo.
These are
Discontinued Lenovo Servers
Lenovo ThinkServer TD100x (4206-11U) Server
Lenovo ThinkServer TD100 (6419-14U) Server
Lenovo ThinkServer RD120 (6446-12U) Server
Lenovo ThinkServer RS100 (6436-14U) Server
Lenovo ThinkServer TS100 (6434-11U) Server
Lenovo ThinkServer RD240 Server

The Current Available Servers from Lenovo are;
New Model Rack Servers
ThinkServer RS140
ThinkServer RD340
ThinkServer RD440
ThinkServer RD540
ThinkServer RD640 

New Model Tower Servers
ThinkServer TS140
ThinkServer TS440
ThinkServer TD340 


We'll have a need for a smaller system with Single Quad Core Processor and 8GB - 12GB ram, plus 4 Drives...

Our Larger units will be Dual Quad Core, and 16GB/24GB Ram and eight drives....

Has any of these systems been verified compatible with Ubuntu?

Any thoughts or comments are appreciated

---

### Post by tgalati4 on 2014-08-19
I presume these are used servers.  I would disassemble them and clean them thoroughly, then check the voltages on the power supplies--a good voltmeter is needed.  Reseat the RAM and all cables.  Get new hard drives if possible, otherwise check the dates and power-on hours of the drives and use the newest to actually hold the OS.

Update the BIOS on the machines to the latest found on the IBM website.  It is easier to do it now than after you have put the machines into production. Download and burn a disk of IBM utilities for your hardware--diagnostics, BIOS flasher, and other utilities which will come in handy later--when you really need them. 

Run memtest on the cleaned-up machines for 30 complete cycles.  Keep a spare machine for a hot spare.  Since these machines are out of warranty, it may be difficult to get parts or service so having a cleaned-up, verified spare will help reduce downtime.  It could even be a running spare using checkpointing, but having it asleep will reduce the aging of the electronics so you can wake it when you need it.

Get a decent UPS to protect your older hardware.  If you have dual power supplies, I would remove one and bag it for a hot spare.  Having two power supplies running all the time uses more power and ages out the power circuitry on your spare PSU which will fail when you really need it.  They will be expensive and hard to find in a few years--so you might start searching now to pick up a few spare PSU's and hard drives.

Since IBM runs and develops linux on its hardware, you should have little problem getting any flavor of Ubuntu to run.  There may be some IBM-provided utilities provided in Red Hat that can be helpful, but some of those you can port to Debian and run.  

Post your installation experiences to this thread.

---

### Post by Earl_Wertheimer on 2014-10-29
I have installed Ubuntu 12.04 and 14.04 LTS server on the TS440 (and earlier TS430) without problems.
My usual setup is 8GB RAM and a set of 500GB or 1TB drives with RAID1

Note: I used software RAID1 to mirror the drives.

The RS140 I am currently installing does not seem to like the built-in RAID controller, so it's back to software RAID.
Note: The RS140 only has space for 2 x 3.5" drives and a single PSU.

The TS130 that was setup with hardware RAID1 did not work. 
I had to reinstall using software RAID.

---

### Post by jason153 on 2014-12-05
Curious of any updates to this thread.  We are in the same boat.  We are a Lenovo reseller and have recently started using a ubuntu based backup solution.  We have successfully tested on a couple of models of lenovo servers, but are having issues with an RD340 at the moment.  Anyone had any experience with this model?

---

### Post by jhony2 on 2015-02-09
Good morning, I´m from Colombia. I have the same problem. What was your experience with this problem? I have a RD430 ThinkServer and I Can´t install Ubuntu Server. Thank you very much.

---

### Post by gacollazos on 2015-03-19
Regards,
I have the same issue when try to install Ubuntu Server 14.10 on RD340 over ssd, when RAID controller is disabled from BIOS the installing process don't recognize ssd and ask for driver

---

### Post by tgalati4 on 2015-03-19
Some IBM servers will only work with Red Hat or Centos.  Something to do with Big Endian verus Little Endian file system.  It's possible to upgrade the firmware to make them compatible with Ubuntu/Debian, but that you will have to research.

---

### Post by obecker on 2015-08-04
> **jason153 said:**
> Curious of any updates to this thread.  We are in the same boat.  We are a Lenovo reseller and have recently started using a ubuntu based backup solution.  We have successfully tested on a couple of models of lenovo servers, but are having issues with an RD340 at the moment.  Anyone had any experience with this model?

HI Everyone,

This is a known BUG in Ubuntu and supposed to be fixed with the latest Version 14.04.2 LTS.  
We ran with out RD340 into the same issue that we where unable to install the GRUB in the MBR or Partition Table.

Wednesday the 5th of August 2015 we will do test if this fix got correctly applied from Ubuntu or not.

---

