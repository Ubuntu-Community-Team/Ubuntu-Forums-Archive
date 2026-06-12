---
title: "Linux on cable box?"
date: 2015-02-19
forum: Hardware
---

### Post by Jakesploder on 2015-02-19
I found a direcTV hr24-100 HD DVR at a garage sale and it was free so i got it. It is pretty useless because i have fios (cable). I was wondering if it was possible to get xbmc or ubuntu TV or even debian running on it. Thanks!

---

### Post by tgalati4 on 2015-02-19
Get some security screwdriver bits and open it up.  See if you can find the type of processor.  You might have to remove a heat sink.  Do a web search on that model DVR and see what comes up.  Include the work "hack" in your search to narrow the responses.  If nothing else, the hard drive (250GB) can be repurposed.  The power supply can be used for RaspberryPi's and Arduinos (5 VDC if you can find the leads) and other devices that use 12VDC.  

Some examples:  [http://www.tivocommunity.com/tivo-vb/showthread.php?t=301286](http://www.tivocommunity.com/tivo-vb/showthread.php?t=301286)

You can use it as an over-the-air ATSC tuner, but it probably only has standard definition outputs.

Transfer the movies on the hard drive to your computer:  [https://www.youtube.com/watch?v=k2vLSCCG-gU](https://www.youtube.com/watch?v=k2vLSCCG-gU)

To put linux on it, you would need to find a way to get the box into an "upgrade firmware" mode and load a new linux-friendly firmware that would be able to read a linux file system on the disk.  This is not trivial, nor do I think this has been done for this box.

---

### Post by Jakesploder on 2015-02-19
Ok, i found that it has a broadcom bcm7335rkfsba33g cpu. Someone said that its either ARM or MIPS. I sure as hell can't tell. Does anyone know? Oh, and what if i used the Multi arch debian iso? how would i boot this and would it support this CPU?

---

### Post by tgalati4 on 2015-02-20
You might be able to load firmware on it in a similar fashion to a router--read the hardware wikis at [http://dd-wrt.com](http://dd-wrt.com).  Many routers use Broadcom bcm processors, which I believe are a RISC (reduced instruction set computer) processor based on the MIPs architecture.  So if you follow the bcmxxxx reset procedures, you might get it into load firmware mode and then put an appropriate linux-friendly firmware on it.  It's worth a shot.

There's a lot of stuff on the processor:

[http://www.broadcom.com/products/Satellite/Satellite-Set-Top-Box-Solutions/BCM7335](http://www.broadcom.com/products/Satellite/Satellite-Set-Top-Box-Solutions/BCM7335)

[http://pinout-circuits-images.dz863.com/395/BCM7335.jpg](http://pinout-circuits-images.dz863.com/395/BCM7335.jpg)

Figure out how to communicate to it through the JTAG interface.

For comparison, a 450 MHz RISC processor is approximately a 900 MHz Pentium in performance, so better than a RaspberryPi, but slower than most desktop PC's.

---

### Post by Jakesploder on 2015-02-20
Apparently it downloads the firmware from the Satilite. Maybe if i could get it into a custom boot option i could install a boot loader... i'm surprised that nobody else has tried to do this

---

### Post by Jakesploder on 2015-02-20
Oh, and I dont really understand what JTAG is, but the only plugs it has (inside the unit and outside)  Sata, 2 USB ports, eSata and ethernet.

---

### Post by Jakesploder on 2015-02-20
I found on this page [http://www.broadcom.com/products/Satellite/Satellite-Set-Top-Box-Solutions/BCM7335](http://www.broadcom.com/products/Satellite/Satellite-Set-Top-Box-Solutions/BCM7335) that it is a MIPS cpu. Im still trying to find a way to boot off another device other than the internal flash memory.

---

### Post by Jakesploder on 2015-02-20
OK, so back on OS X and I'm trying to mount the internal drive. I'm using fuse, and the partition is XFS, at least that is what linux tells me. it won't mount because there's no XFS signature. How do i bypass this? if i can read what is on the drive maybe i could get more info about how to boot another os on this thing.

---

### Post by tgalati4 on 2015-02-21
Take an old PC, put BSD on it and try hooking the drive up to it.  It's possible that the OS is a BSD-varient.  Plug in an ethernet port and try pinging it and see what services are available through the ethernet.  On bcm routers, to get them into firmware mode, you hold down the reset button for 30 seconds, pull power while still holding the reset buttom, then power on, while still holding the reset button.  A menu pops up that says select firmware file to upload.  If you upload a linux-friendly bootloader, then you could probably run just about any linux distro that is compiled for MIPs.

I'm sure you can find the JTAG tools needed to poke this bcm7335 processor:  [http://en.wikipedia.org/wiki/Joint_Test_Action_Group](http://en.wikipedia.org/wiki/Joint_Test_Action_Group)

---

### Post by Jakesploder on 2015-04-07
Thank you guys for all your help, i could not find a way to get linux running on this box to save my life, although i did make use of it (the case at least): i took everything out of it, put my raspberry pi inside of it and loaded openelec on it. And, i also got the HDD out which was 500 GB!

---

### Post by tgalati4 on 2015-04-07
Were you able to access any files on the hard disk to determine the file system?

---

