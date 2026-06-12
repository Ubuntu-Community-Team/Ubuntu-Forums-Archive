---
title: "Agere Systems WinModem 56k (rev 01)"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by Upliftor on 2007-01-03
My PC: Amd 400Mhz, 160 Mb Ram, 4 Gb HDD
OS: Xubuntu 6.10

Can't get Agere Systems WinModem 56k (rev 01) to work!

Where can I find drivers? And how can I install them? (I'm really a new one, facing with Linux)

Heeelp, please!!! :(

---

### Post by Afishionado on 2007-01-03
[http://linmodems.org/](http://linmodems.org/)

Under the "Status" header, click the link for the scanModem tool. It will tell you what chipset your driver has and how to get a driver for it.

(BTW, I've gotten the Agere Winmodem in my laptop to work under Linux, so I'd say the odds are in your favor.)

William

---

### Post by Upliftor on 2007-01-03
> **Afishionado said:**
> [http://linmodems.org/](http://linmodems.org/)

Under the "Status" header, click the link for the scanModem tool. It will tell you what chipset your driver has and how to get a driver for it.

(BTW, I've gotten the Agere Winmodem in my laptop to work under Linux, so I'd say the odds are in your favor.)

William

Well, the name "Agere Systems WinModem 56k (rev 01)" is copied from scanModem tool report. And I even found drivers (here is the link [http://www.heby.de/ltmodem]("http://www.heby.de/ltmodem") ]. But I don't know , what version should I download for Xubuntu 6.10, and how to install this drivers (what I should do,for example, with

 [   ] BreezyGCC_3.4_i386.tar.gz             05-Jun-2006 08:22  3.6M  
[   ] ltmodem-2.6.10-5-386_8.26b1_i386.deb  13-Mar-2006 15:05  401K  
[   ] ltmodem-2.6.10-5-386_8.31b1_i386.deb  13-Mar-2006 15:10  397K  
[   ] ltmodem-2.6.12-9-386_8.26b1_i386.deb  11-Feb-2006 22:52  401K  
[   ] ltmodem-2.6.12-9-386_8.31b1_i386.deb  12-Jan-2006 23:03  397K  
[   ] ltmodem-2.6.12-10-386_8.26b1_i386.deb 11-Feb-2006 21:27  401K  
[   ] ltmodem-2.6.12-10-386_8.31b1_i386.deb 12-Jan-2006 22:52  397K  
[   ] ltmodem-2.6.12-10-686_8.31b1_i386.deb 12-Jan-2006 22:55  397K  
[   ] ltmodem-2.6.12-10-k7_8.31b1_i386.deb  1

It's very difficult after Windows XP :(  But I want to make my modem work.

---

### Post by thhp on 2008-01-08
I have a " Agere Systems WinModem 56k (rev 01)" in my Thinkpad T23 which I'm trying to get going. I thought I'd post what I've found so far in case it is of use to you.

First of all I found, via linmodems, this site which provides a driver and userspace helper application for the modem device:

[INDENT][http://martian.barrelsoutofbond.org/index.html](http://martian.barrelsoutofbond.org/index.html)[/INDENT]

I downloaded this tarball of source (the most recent release):

[INDENT][http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061203.tar.gz](http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061203.tar.gz)[/INDENT]

I untarred this as follows:

```
$ tar -xzf martian-full-20061203.tar.gz
```

then changed to the new 'martian' directory and built the source:

```
$ cd martian && make all
```

If you don't have any development tools installed you will need to install them to do this. I believe the package 'build-essential' should suffice, but I sorted that out so long ago I've forgotten exactly what I had to do!

For my 7.10 install, running a 2.6.22-14-generic kernel, the source built successfully. At this point you should have a kernel-space driver module in the 'kmodule' directory called "martian_dev.ko", and a userspace tool in the 'modem' directory called "martian_modem". 

To load the kernel driver:

```
$ sudo insmod kmodule/martian_dev.ko
```

And to run the userspace helper application:

```
$ sudo ./modem/martian_modem
```

This appears to all run OK on my machine although I haven't tried it with any PPP tools or a phone line yet. Hope it is of some help getting you a bit closer to up and running.

Good luck!

---

### Post by Yellow Pasque on 2008-01-08
> **Upliftor said:**
> what I should do,for example, with

[   ] BreezyGCC_3.4_i386.tar.gz             05-Jun-2006 08:22  3.6M  
[   ] ltmodem-2.6.10-5-386_8.26b1_i386.deb  13-Mar-2006 15:05  401K  
[   ] ltmodem-2.6.10-5-386_8.31b1_i386.deb  13-Mar-2006 15:10  397K  
[   ] ltmodem-2.6.12-9-386_8.26b1_i386.deb  11-Feb-2006 22:52  401K  
[   ] ltmodem-2.6.12-9-386_8.31b1_i386.deb  12-Jan-2006 23:03  397K  
[   ] ltmodem-2.6.12-10-386_8.26b1_i386.deb 11-Feb-2006 21:27  401K  
**[   ] ltmodem-2.6.12-10-386_8.31b1_i386.deb 12-Jan-2006 22:52  397K  **
[   ] ltmodem-2.6.12-10-686_8.31b1_i386.deb 12-Jan-2006 22:55  397K  
[   ] ltmodem-2.6.12-10-k7_8.31b1_i386.deb  1

Use the one in bold.

---

