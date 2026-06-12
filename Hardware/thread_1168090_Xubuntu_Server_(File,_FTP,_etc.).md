---
title: "Xubuntu Server (File, FTP, etc.)"
date: 2009-05-23
forum: Hardware
---

### Post by Tronyx on 2009-05-23
Please forgive me if this is in the wrong section or has an inappropriate prefix as this is my first post.  I decided a short while ago that I want to build a nice little file server for my next project.  I decided that I would like to use Linux over Windows and started looking around online for a guide on how to do so.  I came across Glider's two Build Your Own Server guides and immediately made the decision to follow his guides. Before I get into my issue I want to list the hardware for the build:

BioStar T-Series TP43DA2-A7 775 ATX Motherboard
Intel E6600 Core 2 Duo Processor
3Gb Generic (I think it is Hyundai, lol) DDR2 800 RAM
EVGA 512Mb PCI-e x16 Video Card
80Gb WD OS Drive
4 - 1TB WD Caviar Green Storage Drives in an Addonics Disk Array
Generic DVD-R/CD-RW Drive
Promise Fast Trak TX4650 PCI-e SATA II RAID Controller Card
Corsair 650w PSU

I got it all assembled (minus the RAID Card) 2 days ago, installed Xubuntu 9.04, updated it and made sure that it was running smoothly.  The RAID Card showed up yesterday, I installed it, hooked up the drives and fired it up.  I followed the instructions that came with it on how to setup the RAID 5 within, what I can only guess is, the RAID Cards BIOS.  Please correct me if I am wrong with that thought. The machine still boots wonderfully and the system recognizes the drives, but the only problem is that it sees them as 4 separate 1TB drives and not as the RAID.  Well, I admit I had to smack my forehead and say "Drivers! Duh!".  Herein lies my issue.  The only drivers that came on the CD are for Red Hat Enterprise Server, SUSE Linux Enterprise Server and Windows.  I went online to the Promise site and grabbed the Partial Open Source drivers that were listed under "Other" since I do not have RHES or SLES. Now, I'm not totally new to Linux, but I am far from anywhere close to being decent with it. I attempted to follow the read-me that was with the drivers, but I could not get to work. I've been banging my head against the freakin' wall for going on 6 hours now trying to get this to work.  ](*,)

I am looking for some advice and/or instruction as to what to do.  I really want to follow the guides that Glider wrote since it is exactly what I want.  Any and all advice/comments are welcome.

Thank you for taking the time to read this, I know it's long.

Chris aka Tronyx

---

### Post by albinootje on 2009-05-23
> **Tronyx said:**
> 
the only problem is that it sees them as 4 separate 1TB drives and not as the RAID.  

A quick search makes me believe that this RAID card is not supported by default in (X)Ubuntu, see here :

[http://ubuntuforums.org/showthread.php?t=1157745](http://ubuntuforums.org/showthread.php?t=1157745)
[http://ubuntuforums.org/showthread.php?t=1148734](http://ubuntuforums.org/showthread.php?t=1148734)

With those instructions in there you seem to be able to compile a new kernel, and have it supported.

---

### Post by Tronyx on 2009-05-23
> **reznorio said:**
> Hi,

You downloaded the kernel source and extracted it in /usr/src?
you link it to /usr/src/linux?
you copy over config from boot to .config in the /usr/src/linux dir?
run make menuconfig save it and then quit then run make. It should fix those header errors you're getting (I got).

ReZ

You mean those instructions?  I have no idea how to even begin to recompile the kernel...

Do you have any suggestions of what I could/should do?

Chris

---

### Post by albinootje on 2009-05-23
> **Tronyx said:**
>  Do you have any suggestions of what I could/should do?

Can you ask the people in that other thread where others are compiling a kernel for that RAID card ?

Which Xubuntu release are you using by the way ? 8.04 ? 9.04 ?

And.. you can try FreeBSD instead of Linux.
By default FreeBSD has more support for various RAID cards is my impression (I have experience with an older Fasttrack card, and a 3Ware card, which worked out of the box in FreeBSD, and not out of the box in Linux).

See here for FreeBSD and FreeBSD based downloads : 
[http://www.freebsd.org/where.html](http://www.freebsd.org/where.html) --> FreeBSD 7.2-RELEASE
[http://www.pcbsd.org/](http://www.pcbsd.org/)
[http://www.desktopbsd.net/](http://www.desktopbsd.net/)

---

### Post by Tronyx on 2009-05-23
It's Xubuntu 9.04.  It seems like if I want to follow the really nice guide from Bit Tech I will have to go with a mdadm or similar software raid setup.  Only issue with that is the performace drop over a hardware RAID.  Unless I am completely misinformed...

I will ask the individual that posted those directions about it.

Chris

---

