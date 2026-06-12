---
title: "about to give up on installing"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by macjohn on 2009-04-11
MSI K8N Neo V2.0 motherboard
Nvidia 6200 256mb video card
Athlon64 3200 processor
2 gigs of PC3200 RAM
no PCI cards plugged in during installation

Currently have OSX 10.5.2 and Windows XP installed on different SATA drives on this PC and running VERY smooth.  Have an IDE drive I'm trying to install Linux to.  Have had success with installing (and running) on my old P4 but now I'm trying to get it going on my athlon.

I usually install with my sata drives disconnected... just to reduce risk.

Have now tried to install:
Ubuntu 8.10 AMD64
Ubuntu 8.10 x86
Ubuntu alternative 8.10 AMD64
Ubuntu alternative 8.10 x86
Ubuntu default downloaded 8.10 CD
Ubuntu default downloaded 8.04 CD
Ubuntu alternative 8.04 x86
Debian 5.0 x86
Debian 5.0 AMD64
Linux Ultimate Edition 2.1
Linux Mint 6
FreeBSD 7.1
SUSE 11.1 x86
SUSE 10.3 x86

Here is how the installation typically goes:

boots fine, cd loads, select default install, installs and either crashes on boot or right after boot while doing something (hard freeze).

The exception is the default Ubuntu CD's... they don't even install and freeze shortly after initiating the install.

Suse had a check system option that I initiated after the first crash.  It claimed it would check my hardware for problems.  It ended and reported a 'kernel error' and gave a version that I didn't write down. 

Should I just be happy with my dual boot or should I continue going for the three way?

---

### Post by ninjapirate89 on 2009-04-11
Are you sure it's not a hardware problem? It seems to me that if none of those versions worked for you then this must be the case.

---

### Post by abn91c on 2009-04-11
when using the ubuntu cd's it is best to start a live cd session first then run the installation from the desktop icon. That way you can test your hardware first and not doing a blind installation. Many users here have the same problem because they select install at the menu instead of the "try ubuntu without changing your PC" option

---

### Post by macjohn on 2009-04-11
> when using the ubuntu cd's it is best to start a live cd session first then run the installation from the desktop icon. That way you can test your hardware first and not doing a blind installation. Many users here have the same problem because they select install at the menu instead of the "try ubuntu without changing your PC" option

ah, forgot to mention that I did try that option with the downloaded Ubuntu CD's.  It typically froze at some point during the install, usually while selecting the time zone... which was also the common place where all the other installs froze for Ubuntu.

> Are you sure it's not a hardware problem? It seems to me that if none of those versions worked for you then this must be the case.

That would be my thought as well... if I hadn't spent two weeks working on the OSX installation and have it running perfectly and crash free... and the XP installation has been going strong and relatively crash free for a year or so.

---

### Post by cariboo on 2009-04-11
I have an MSI motherboard of about the same vintage, with some of the LiveCD's I had to start in safe graphics mode to  get to the desktop. Press F4 at the menu and select safe graphics mode, then continue booting.

Jim

---

### Post by macjohn on 2009-04-12
> I have an MSI motherboard of about the same vintage, with some of the LiveCD's I had to start in safe graphics mode to get to the desktop. Press F4 at the menu and select safe graphics mode, then continue booting.

Thanks for the suggestion!  Just tried that with Ubuntu 8.10.  Starts loading, the bar goes all the way to complete, then the screen blanks and I have a blinking cursor in the upper left hand corner and it's frozen.

---

### Post by cariboo on 2009-04-12
The only other thing I can suggest is to use the alternate install cd. This is a text based installer, that doesn't access the graphicas subsystem. It does a full install and  after a reboot you should be at your desktop. You can get the alternate install iso [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

Jim

---

### Post by macjohn on 2009-04-12
> The only other thing I can suggest is to use the alternate install cd.

Thanks, tried that many times.  It installs fully, and craps out within a minute of being booted into the live system, usually during network configuration.

---

### Post by asherayer on 2009-04-12
I have a similar setup and the same problems. I've tried the live cd, running without installing and install along with any other option like safe graphics. All freeze while the bar is loading.

Then I tried the alternate install cds and was able to get further but then it would freeze and ask me to insert the install disc. After searching the forums I found that this was from a glitch with NEC drives. 

So I installed another drive and was able to get even further being able to actually put in my name and password. But then of course even further down the line it freezes again.

Each time it "freezes" the disc drive stops working and I'm unable to eject. 

I also tried booting from usb using UNetbootin but cmos only has boot options for hard disk, optical, and removable. I set it to removable but it wouldn't boot off my usb even though I saw it recognized it during start up.   

I'm using an 
Asus K8N-DL  motherboard
Nvidia 6800 256mb video card
Opteron 480 processor
2 gigs registered RAM

I'm totally desperate and would appreciate any help

---

### Post by nitewing98 on 2009-04-12
> **macjohn said:**
> 
Have now tried to install:
Ubuntu 8.10 AMD64
Ubuntu 8.10 x86
Ubuntu alternative 8.10 AMD64
Ubuntu alternative 8.10 x86
Ubuntu default downloaded 8.10 CD
Ubuntu default downloaded 8.04 CD
Ubuntu alternative 8.04 x86
Debian 5.0 x86
Debian 5.0 AMD64
Linux Ultimate Edition 2.1
Linux Mint 6
FreeBSD 7.1
SUSE 11.1 x86
SUSE 10.3 x86
Could it be your disc burner?  I'm assuming you burned all these disks yourself.  I just recently had a drive that wouldn't read its own burned disks (how weird is that?).  What about the media itself?  Are they all the same brand CD?

Also try posting the relevant make/brand of the hardware involved, it could be related to a pieces of hardware that doesn't play well with linux.  For starters I'd not only unhook the SATA drives but anything else you don't need during the install (webcams, microphones, usb devices, etc.).

Kevin

---

### Post by abn91c on 2009-04-12
try Mandriva 2009 KDE version, it older hardware friendly

---

### Post by macjohn on 2009-04-13
> try Mandriva 2009 KDE version, it older hardware friendly

Well, that did it.  I'm typing to you from my Mandriva 2009 KDE installation right now.  I have sound, network (obviously)... haven't played with multiple monitors yet but seems like I'm on the road.  Next step is to hook up my other two drives and make sure I can tri-boot from my windows boot loader.

Thanks for all the help!

---

