---
title: "Don't buy P45 chipset (especially Asus P5Q)"
date: 2008-08-15
forum: Hardware
---

### Post by gdp77 on 2008-08-15
It is COMPLETELY incompatible with Ubuntu. Nothing on this mobo (Asus P5Q) works with Ubuntu. sata problem, marvell controller problem, atheros problem...

Stay away!!!

P.S. F you asus!

---

### Post by starcannon on 2008-08-15
gdp77 I feel your frustration, that said, Asus did release some really cool umpc's with linux as the oem installed OS.

So hang in there, I think perhaps they will get more friendly with the linux community as time goes on, we made them a wack of money by making the Asus Eee the overnight success that it is.

---

### Post by EmmEff on 2008-08-15
This is more of an Intel issue, than ASUS since it's Intel's P45 chipset.  I am surprised to hear it is incompatible, though.

To the OP, which version of Ubuntu are you installing?

---

### Post by ktbrodal on 2008-08-15
Do you have any suggestions for a good alternative MB at about the same prize, then?

---

### Post by stchman on 2008-08-15
> **gdp77 said:**
> It is COMPLETELY incompatible with Ubuntu. Nothing on this mobo (Asus P5Q) works with Ubuntu. sata problem, marvell controller problem, atheros problem...

Stay away!!!

P.S. F you asus!

I own the Asus P5K (Intel P35 chipset) and it works perfectly under Hardy.

---

### Post by newguy1950 on 2008-08-15
At the moment the Asus P5Q-E a real pain to use =/ I get nothing but libata errors when booting up. Still some people report that they got it working, I'm trying to figure out what they do different. I'm afraid it may be the EVMS...

---

### Post by gdp77 on 2008-08-16
> To the OP, which version of Ubuntu are you installing?

8.04 of course. Tried both 32 and 64bit versions.

> Do you have any suggestions for a good alternative MB at about the same prize, then?

P35 works with Ubuntu PERFECT and is a very good chipset (very good o/c and stable as well). The only reason to buy P45 is if you need 2 x PCIE16x slots (for CF)

> At the moment the Asus P5Q-E a real pain to use =/ I get nothing but libata errors when booting up. Still some people report that they got it working, I'm trying to figure out what they do different. I'm afraid it may be the EVMS...

+1  mate. I am afraid that we are hopeless at least until 8.10 is released.

---

### Post by ktbrodal on 2008-08-16
> **gdp77 said:**
> P35 works with Ubuntu PERFECT and is a very good chipset (very good o/c and stable as well). The only reason to buy P45 is if you need 2 x PCIE16x slots (for CF)

Any chance you have any experience with the X48-chipset also?

What is the predecessor of X48 btw?

---

### Post by newguy1950 on 2008-08-16
> **gdp77 said:**
> +1  mate. I am afraid that we are hopeless at least until 8.10 is released.

I do not understand the reports of people that got it working without errors, apparently. I've tried every combination of BIOS options I could find so far, tried with kernel 2.6.24 and 2.6.26. No luck. BIOS update did not change anything, either. I've spent more then 25 hours on the issue, without success so far. It's rather frustrating, after having checked the hardware for hours (onboard sound, network chip) and still tripping over an issue like this one (and not even having someone to blame =)).

---

### Post by newguy1950 on 2008-08-17
I seem to have solved the problem on my system, at least it has been running without issues for at least half-a-day so far and is letting me write this posting, which is a new record. A full 1 TB RAID-5 reconstruction also went through without hiccups.

Here's what you need.

1. Kernel 2.6.26-5-generic from Intrepid
2. Correct BIOS Settings.

Set your BIOS to use AHCI, disable unneeded extras. I use ACPI 2.0 as well.

Installing the kernel is another matter. Compiling a backport is not recommended, as it is quite complicated - the binary packages for Intrepid should work fine. In short (I won't give a long explanation, as I do not recommend the faint of heart or new users to try this), easiest way to get it working is to update, dist-upgrade; then add Intrepid repositories, install the packages linux-image-2.6.26-5-generic, gcc (this will update to gcc 3.4) and nvidia-glx-177.

(Gcc 3.4 is needed, because the kernel was compiled with it and will usually reject modules not compiled with the same version.)

Once all the packages are installed, remove the Intrepid repositories and update again. You now have a new kernel, new libc with a bit of fluff, and new gcc installed. If you use ATI, you don't need nvidia modules, if you bought an ATI card you're <snip> in so many ways that you should stick to 2D anyways.

Do not boot with irqpoll. It messes up things again on my system and is not needed.

---

### Post by Knighthammer on 2008-08-22
I so wish I would have seen these posts before I bought my P5Q-Pro. I wanted it because I heard it had good Cross-Fire support under Windows. But when I went to dual-boot with 8.04 failure! The Windows working well is the only bright side to this board - I agree with OP, big dissapointment!

---

### Post by Marshal0505 on 2008-08-22
I'm happy with the way my p5q pro runs Ubuntu Hardy.Solved all problems with some fidling around and the Atheros ethernet driver was found with Google.
In short: i'm loving the experience this board gives me.

---

### Post by grigio on 2008-08-27
are u able to control the fan with this mobo? how?

---

### Post by albaloo on 2008-09-01
I am running hardy with P5Q deluxe without any issues what so ever.  It detected the HD controllers, sound card, and network drivers without any intervention on install.  The only thing I had to change was to set the SATA setting in the bios to AHCI which I had looked up prior to buying the board.  Not sure what kind of problems you're having.  Asus's Q fan control is running fine.  Just set it in the bios.

---

### Post by grigio on 2008-09-02
> **albaloo said:**
>  .. Not sure what kind of problems you're having.  Asus's Q fan control is running fine.  Just set it in the bios.

Yeah, I did it, but with **Asus AI suite**, you can dinamically change cpu frequency and fan speed without reboot and change the bios..

In Linux there is **fancontrol**, but it doesn't work on P5Q

---

### Post by Zzl1xndd on 2008-09-04
I also have a P5Q Pro, Board works like a dream, only thing I had to do was download the driver for the network card, I do have a small sound problem were sometimes it will cut out and not come back but its rather few and far between and Im hoping with 8.10 it wont be an issue anymore.

---

### Post by toxicfeet on 2008-09-10
> **newguy1950 said:**
> I seem to have solved the problem on my system, at least it has been running without issues for at least half-a-day so far and is letting me write this posting, which is a new record. A full 1 TB RAID-5 reconstruction also went through without hiccups.

Here's what you need.

1. Kernel 2.6.26-5-generic from Intrepid
2. Correct BIOS Settings.

Set your BIOS to use AHCI, disable unneeded extras. I use ACPI 2.0 as well.

Installing the kernel is another matter. Compiling a backport is not recommended, as it is quite complicated - the binary packages for Intrepid should work fine. In short (I won't give a long explanation, as I do not recommend the faint of heart or new users to try this), easiest way to get it working is to update, dist-upgrade; then add Intrepid repositories, install the packages linux-image-2.6.26-5-generic, gcc (this will update to gcc 3.4) and nvidia-glx-177.

(Gcc 3.4 is needed, because the kernel was compiled with it and will usually reject modules not compiled with the same version.)

Once all the packages are installed, remove the Intrepid repositories and update again. You now have a new kernel, new libc with a bit of fluff, and new gcc installed. If you use ATI, you don't need nvidia modules, if you bought an ATI card you're f.ucked in so many ways that you should stick to 2D anyways.

Do not boot with irqpoll. It messes up things again on my system and is not needed.

What are you using to do all of that, uck-gui? Are you using a 8.04 or 8.10 disk?

---

### Post by pigeonjim on 2008-09-11
I love my p5q deluxe however I too cant get ubuntu to install; It doesnt see my sata hard drive. :-(
I can not change to ahci in the bios because i already have xp installed (which i use for games) and I didnt do the F6 thing because I dont have a floppy drive. I have tried and failed to use many methods to change my xp to ahci without reinstalling and I have been unsucessful. 
Is there any other way to get Ubuntu to recognise my hard drive so I can install?

---

### Post by jykke on 2008-09-16
I managed to install Vista64 and Ubuntu 8.04.1 with RAID option set on the P5Q Pro motherboard. 

I have two 500 gb harddrivers. And they make up for one Raid0 and one Raid1 disk as and Raid array. 

Here is a tutorial that I used: [http://hol.net.nz/blog/kubuntu-with-fakeraid](http://hol.net.nz/blog/kubuntu-with-fakeraid)

Before the part of sudo mount --bind /dev /target/dev you must mount the correct partition to target 

sudo mkdir /target
sudo mount -t ext3 /dev/mapper/via_hfciifae7 /target

Also before you can start the process you must have an usb stick or other means to install this LanDriver:

[http://ubuntuforums.org/showpost.php?p=5456722](http://ubuntuforums.org/showpost.php?p=5456722)

Also I had installed Vista first. And if you happend to break it's booting :) you can use the Vista installation DVD to correct this by using the repair options on the DVD.

---

### Post by Therion on 2008-09-16
> **pigeonjim said:**
> I love my p5q deluxe however I too cant get ubuntu to install; It doesnt see my sata hard drive. :-(
I can not change to ahci in the bios because i already have xp installed (which i use for games) and I didnt do the F6 thing because I dont have a floppy drive. I have tried and failed to use many methods to change my xp to ahci without reinstalling and I have been unsucessful. 
Is there any other way to get Ubuntu to recognise my hard drive so I can install?
I just did a new build on an Asus P5Q (Intel P45 chipset) and I'm dual-booting XP and Ultimate Edition (a Hardy Heron Ubuntu fork).  I have a Western Dig Raptor (SATA) as my primary drive, and WD SATA slave drive installed.  I also have AHCI enabled in the BIOS.  

The P5Q does seem odd in regard to the AHCI thing.  When I enable that option (AHCI), Windows does *not* see my SATA slave-drive but Ubuntu *does*.  Disable that option and Windows sees the SATA slave-drive, but Ubuntu does not (!!??).

I am able to boot off of the SATA primary drive, however, regardless of the AHCI setting in the BIOS.

---

### Post by brdokoky on 2008-09-16
P5Q is good . When you need to install winxp on ahci , just make your own cd of winxp with ahci driver. After you can very easy install ubuntu. Network to work , prepare from windowsxp- download the driver with manual howto, and that's it. P5Q is superb:)

---

### Post by Makere on 2008-09-17
I would be interested in how raid5 works on ubuntu and asus p5q(-e)? Because I'm planning on to build my next home server based on those. Thanks in advance!

---

### Post by baserunner_ams on 2008-09-21
Hi all,

i have bught the P5Q Pro.

I can install windows 2003 64bit and vista 64bit without any trouble.
I can install Ubuntu 8.04.1 32bit without any problems (nic driver downloaded from asus)

When trying to install Ubuntu 64bit my systems hangs after recognizing the usb ports and devices.

My setup:
P5Q pro
Intel Core 2 Quad Q6600
4 GB RAM
3* 500GB Sata HD (Barracuda)

I will try this link/tutorial:
[http://ubuntuforums.org/showthread.php?t=890604]("http://ubuntuforums.org/showthread.php?t=890604")
for the raid setup

---

### Post by nicbul on 2008-09-28
I too am building a P5Q based system (Q6600, 4gb ddr2 1066, 500gb SATAHD, 9600GT) and have been researching its compatability with Ubuntu 8.04 64bit.  It appears that there are potentially only three issues with the board:  SATA drives, USB detection and on-board LAN.

SATA solution:
[http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450](http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450)

SATA and USB solution:
[http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html](http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html)

Steps to the LAN solution:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

From what I gather from these posts, it's a matter of changing a couple of BIOS settings and then compiling the ethernet drivers.

I believe the drivers are downloaded from here:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

After selecting the correct motherboard model and operating system, in the section 'Other' is a Linux driver to download.  I assume that this is for the LAN and that one would follow the steps for compiling it in the ubuntuforum post above.


I also have a newb-type question for the board:  Does the latest bios version include all other previous BIOS updates or does one have to flash each update to get to the current version?  AND!  Do any of the BIOS versions work best or are most stable with Ubuntu?

---

### Post by ac4000 on 2008-09-29
> **nicbul said:**
> I also have a newb-type question for the board:  Does the latest bios version include all other previous BIOS updates or does one have to flash each update to get to the current version?  AND!  Do any of the BIOS versions work best or are most stable with Ubuntu?

Unless it's a /really/ unusual BIOS (and there's almost no way it is), each flash update completely rewrites the chip (save for the protected part), so you can just jump to the version you want.

I hope everyone who has this board working is right ... just about to order one instead of a P5K to replace my Gigabyte GA-P965-DS3 that, due to a corrupted BIOS flash or something else, is currently a paperweight.

(And thanks to nicbul for listing all the solutions in one place.)

---

### Post by gabba on 2008-09-29
I just bought a P5Q-Pro and it's running fine under Ubuntu Hardy 8.04.1 64bits.

I installed winXP (before ubuntu) in IDE mode, and ExpressGate only works in that mode, so switching to AHCI was out of the question.
[B]
The following allowed me to have a fully functional system while staying in IDE sata mode.[/B]

1. Boot livecd with boot options: **irqpoll all_generic_ide**
(I found this tip on the [french ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1933012#p1933012").)

2. Install Ubuntu

3. Boot with the livecd again, mount the appropriate partition and go edit your grub.lst file to add **irqpoll all_generic_ide** to the boot line. There's a place in the file where you can put these options so that they are automatically appended even if you change kernels.

4. That booted fine, all that was left was to get the network card up: for that I went into Windows XP and downloaded the linux network driver for the P5K-PL (don't ask why they don't provide it for the P5Q). Instructions to compile it are [pretty easy to find]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1894719#p1894719"); after compiling when I tried "make install" it didn't want to, so I manually copied the .ko file to the place it's supposed to end up, and used the **insmod** command to activate it.

5. Everything was working fine, so I upgraded to the latest packages and kernel. I expected having to recompile the network driver, but the network was still working after reboot, so I suspect it was included in later updates. I'll try and remove the special boot options, just in case the new kernel also fixed some things...

EDIT: forgot to mention that my sata hard drive (and DVD writer I believe) are both plugged into the Marvell SATA ports (the different-colored ones).

---

### Post by ac4000 on 2008-10-02
> **gabba said:**
> add **irqpoll all_generic_ide** to the boot line

Perfect!  Worked like a charm.  Thanks, gabba.

---

### Post by gabba on 2008-10-02
> **ac4000 said:**
> Perfect!  Worked like a charm.  Thanks, gabba.

Happy I could help!

One thing bothers me, however: I know those options help, but I have no clue about what they do: can they hamper performance or cause other problems? I'd appreciate if someone experienced could chime in and give us a little more information.

---

### Post by ac4000 on 2008-10-02
> **gabba said:**
> One thing bothers me, however: I know those options help, but I have no clue about what they do: can they hamper performance or cause other problems?

My research indicates that AHCI has two advantages:  hot-swapability and NCQ (native command queing).  Tests are inconclusive as to whether or not this makes much difference in real world performance for most users.  Since the technology is fairly new, the IDE BIOS setting is still often the default, even though AHCI is newer and usually supported (in the hardware).

Now here's where I'm making a reasonable guess:  The Linux kernel expects SATA drives to use AHCI and IDE drives to use IDE, so it cannot find your SATA drives (by default) if they're running in IDE mode.  (This is why I was able to boot without changing anything:  my boot drive is an IDE; but I couldn't see my second drive, which is SATA.)

In order to change this behavior, we can add the options irqpoll and all_generic_ide.  The second option forces the kernel to use IDE mode for everything (and so it finds your SATA drives).  I don't know what the first option does, however; has anyone tried using just the second?  Might give that a shot when I'm back on that computer.

Since XP and ExpressGate (among others) won't handle AHCI without additional help, it's easiest to just leave the system in IDE mode and force the kernel to use that mode (Linux is obviously more trustworthy and adaptable than XP with this sort of thing).  There's a theoretical performance loss (via NCQ) and you lose hot-swabability, but in reality it's probably all the same.

---

### Post by gabba on 2008-10-02
Hey thanks for researching this!

I found the following about irqpoll:
(in this document which lists all kernel parameters:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt))

```
irqpoll		[HW]
			When an interrupt is not handled search all handlers
			for it. Also check all handlers each timer
			interrupt. Intended to get systems with badly broken
			firmware running.
```

Apparently you may need it if several peripherals wrongly share the same irq. I wonder why we're supposed to need it in this case? I have to try without it as well.

---

### Post by RealG187 on 2008-10-02
Isn't ASUS a supporter of Linux?

---

### Post by ac4000 on 2008-10-02
> **RealG187 said:**
> Isn't ASUS a supporter of Linux?
Yes, they seem to be and the PQ5 is no exception.  Installing the network driver was trivial (thanks to posts here and the driver available on the ASUS site), and switching to AHCI solves the SATA drive problem as long as you don't need to dual boot (and, if you're dual booting, you can probably handle adding a few words to the kernel boot line).  Since AHCI is more modern, it almost makes sense that the kernel would default to it.  That said, it would appear that later kernels will detect SATA drives in IDE mode, eliminating the need to switch to AHCI or use the kernel options.  Further, it's almost certain the network driver will be included very soon.

Save for those two minor issues, everything else, including the sound, work right out of the box, which is a hell of a lot more than I can say for XP.  No complaints here, running an open-source kernel/operating system on a chipset that *just* came out.  In fact, I plugged in my old installation's IDE drive and everything booted right up and is running just like before.  (Having used DOS/Windows systems daily from 1985 through 2006, I expected an OS reinstall after switching the motherboard.  But--and this is due to how robust Linux is and how hard the developers work to take advantage of hardware improvements--a few words on the boot line got my second hard drive working and a flash drive and 5 second compilation got my network working.  I consider that pretty damn good.)

---

### Post by StephenKing on 2008-10-12
Hi!

I've bought my P5Q Deluxe ~8 Weeks ago and I'm quite happy with Interpid (using dmraid). Network worked out-of-the-box.

The only problem I have is my sound: ALSA can only be used by one application simultaneously, which is really annoying!
Do you have any tips? What to check? I olny find postings, where sound is not working at all.
A reinstallation didn't help.

Thanks
Steffen

---

### Post by Makere on 2008-10-12
> **StephenKing said:**
> Hi!

I've bought my P5Q Deluxe ~8 Weeks ago and I'm quite happy with Interpid (using dmraid). Network worked out-of-the-box.

The only problem I have is my sound: ALSA can only be used by one application simultaneously, which is really annoying!
Do you have any tips? What to check? I olny find postings, where sound is not working at all.
A reinstallation didn't help.

Thanks
Steffen

Use Pulseaudio.

---

### Post by StephenKing on 2008-10-12
Okay, I will have a try.
I searched how to activate pulse audio, but as I found out that pulse is just an abstraction layer and still needs to use ALSA I thought it might not help.

---

### Post by StephenKing on 2008-10-12
Yeah, it works!

Thanks for your advice!

---

### Post by blackpaw on 2008-11-17
I just found this website on the P5Q-E and AHCI/EHCI/ACPI problems. Apparently he got it solved.
(I just ordered a P5Q-E... *fingers crossed*)

[http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html]("http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html")

Together with the other tips from this fine forum I hope to be able to join the 64-bit age this week. :)

Cheers,


Andreas


P.S. SUCCESS! Following the hints (set SATA to EHCI , disable USB BIOS EHCI Hand-Off and enable ACPI 2.0 support in BIOS) allowed me to install 8.10 x64 without a single glitch. yay! :D

---

### Post by Mguel on 2009-01-10
I just bought the Asus P5Q MoBo (I can still return it)... but I don't know if now a days there is a better alternative in terms of compatibility with 64 bit (k)ubuntu.

**Some one told me that the:**[INDENT] GIGABYTE GA-EP45-DS3L (rev 1.0)
would be a better alternative (which is also available on the store I bought the asus one), but I can't find much info on that.
Edit: found a Phoronix review of this mobo: [http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1)
[/INDENT]**Or maybe another alternative would be the:**[INDENT]ECS P45T-A (V1.0) MoBo

[/INDENT]**The rest of my hardware is:**[INDENT]CPU INTEL CORE 2 DUO E8500 - 3.16 GHZ 1333 MHZ DUAL CORE BOX
nVidia GeForce&#8482; 9800GT 512MB 
Corsair XMS2 DDR2 2Gb (2x1Gb) PC6400C4DHX
500 gb sata2 western digital 7200rpm
TOPOWER M2 600W ATX 12V2.0 20+4 PINES
thermaltake wing RS100
[/INDENT]

---

### Post by Nandro3 on 2009-01-10
Using all the tips i finally got it up and working with all 3 of my sata drives, now I am working on my NTFS firewire drive with all my tunes and my usb audio DAC  anyone use one of these?

---

### Post by HDTimeshifter on 2009-01-11
> **nicbul said:**
> I too am building a P5Q based system (Q6600, 4gb ddr2 1066, 500gb SATAHD, 9600GT) and have been researching its compatability with Ubuntu 8.04 64bit.  It appears that there are potentially only three issues with the board:  SATA drives, USB detection and on-board LAN.

SATA solution:
[http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450](http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450)

SATA and USB solution:
[http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html](http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html)

Steps to the LAN solution:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

From what I gather from these posts, it's a matter of changing a couple of BIOS settings and then compiling the ethernet drivers.

I believe the drivers are downloaded from here:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

After selecting the correct motherboard model and operating system, in the section 'Other' is a Linux driver to download.  I assume that this is for the LAN and that one would follow the steps for compiling it in the ubuntuforum post above.


I also have a newb-type question for the board:  Does the latest bios version include all other previous BIOS updates or does one have to flash each update to get to the current version?  AND!  Do any of the BIOS versions work best or are most stable with Ubuntu?

I did a new build in the beginning of October with an ASUS P5Q Pro, Q6600, Corsair 2x2GB DDR2 800, WD 750GB SATA, ASUS EN9500GT (nVidia) and installed 8.04 64-bit without too much problem.  I'm currently running 8.10 64-bit with latest update.  This was the first PC that I built from scratch as well as my first Linux system.  The first thing I did was flash the BIOS to the latest version.  The only problems I had were having to set the BIOS to start the boot order from the HD rather than floppy->ZIP->CD->HD, and having to compile the Atheros driver to get networking working.  USB support worked with no problems.  I was able to plug in a USB drive with BIOS update downloaded from an XP box to reflash my BIOS.  I also share a USB printer with my Windows network.  I run Sun's xVM Virtualbox with XP SP3 when I need to run Windows stuff.  I'm networked to a Vista SP1 laptop, and a couple of XP SP3 boxes.  My only remaining problems are basically with Ubuntu 64-bit:  occasional breaking of Flash for videos whenever they update, and only 1-way browsing of my Vista laptop (Vista can see Ubuntu, but Ubuntu can't see Vista - Ubuntu/Samba issue).  Also, it seems that whenever an update requires a reboot, my system will reboot but hang on the Ubuntu startup screen with the progress bar solid green, then pushing the hardware reboot button reboots it into low screen resolution and I have to reset my nVidia X Server Settings back to 1600x1200.

---

### Post by Makere on 2009-01-12
> **HDTimeshifter said:**
> I did a new build in the beginning of October with an ASUS P5Q Pro, Q6600, Corsair 2x2GB DDR2 800, WD 750GB SATA, ASUS EN9500GT (nVidia) and installed 8.04 64-bit without too much problem.  I'm currently running 8.10 64-bit with latest update.  This was the first PC that I built from scratch as well as my first Linux system.  The first thing I did was flash the BIOS to the latest version.  The only problems I had were having to set the BIOS to start the boot order from the HD rather than floppy->ZIP->CD->HD, and having to compile the Atheros driver to get networking working.  USB support worked with no problems.  I was able to plug in a USB drive with BIOS update downloaded from an XP box to reflash my BIOS.  I also share a USB printer with my Windows network.  I run Sun's xVM Virtualbox with XP SP3 when I need to run Windows stuff.  I'm networked to a Vista SP1 laptop, and a couple of XP SP3 boxes.  My only remaining problems are basically with Ubuntu 64-bit:  occasional breaking of Flash for videos whenever they update, and only 1-way browsing of my Vista laptop (Vista can see Ubuntu, but Ubuntu can't see Vista - Ubuntu/Samba issue).  Also, it seems that whenever an update requires a reboot, my system will reboot but hang on the Ubuntu startup screen with the progress bar solid green, then pushing the hardware reboot button reboots it into low screen resolution and I have to reset my nVidia X Server Settings back to 1600x1200.

For the resolution/update problem, try installing nvidia drivers with envyng (envyng-gtk in repositorys). As it will install a package that compiles the nvidia drivers automatically whenever you get a kernel update (update that requires reboot).

---

### Post by Imprez on 2009-01-16
> **Makere said:**
> I would be interested in how raid5 works on ubuntu and asus p5q(-e)? Because I'm planning on to build my next home server based on those. Thanks in advance!
I´m having similar plans and would really appreciate if someone have any experience to share about using the onboard RAID-controller for raid5.

---

### Post by RJARRRPCGP on 2009-01-16
Fine here with an Asus P5QL Pro, with Intrepid Ibex. 

Many of the problems probably are related to 8.04 not having support for the chipsets.

---

### Post by Makere on 2009-01-17
> **Imprez said:**
> I´m having similar plans and would really appreciate if someone have any experience to share about using the onboard RAID-controller for raid5.

It didn't work atleast in 8.10 Beta, some googling later it seemed like they had broken the raid5 support with the fix that was applied it 8.04.1. Try googling for general soft raid5 support, and if it works now.

---

### Post by Nandro3 on 2009-01-17
I have had many regular sata issues with my P5Q-E let alone raid.  If you are going for raid I would look for a different board.  Not that it couldnt probably be done, but just to even get the board to see the sata drives it needs to be changed to ACHI along with a few other changes and the ipqpoll all_generic_ide needs to be added to the boot config as well.  Maybe others have done it, but it took me a while and even then I had issues.  I eventually went back to windows 7 on that board.  On my P5E everthing worked right after install, albiet I didnt try raid.  I have read that unless you get a well supported raid card that almost everyone uses software raid which i personally dont like.  If I do raid I want hardware raid.

---

### Post by Mguel on 2009-01-23
> **Mguel said:**
> I just bought the Asus P5Q MoBo (I can still return it)... but I don't know if now a days there is a better alternative in terms of compatibility with 64 bit (k)ubuntu.

Finally I kept the P5Q and it worked as you mentioned me.

Only changed the bios HDD setting from ide to achi... and after a usb not detection I changed the usb setting on bios mentioned on [http://linuxrevolution.blogspot.com/...therboard.html](http://linuxrevolution.blogspot.com/...therboard.html) and that's it... the system working great.

Now I'm trying to activate audio output through hdmi... but it's only an option I would like to have to the 5.1 direct output I have allready working. It's not really an issue.

My whole system:
ASUS P5Q - Intel® P45 / ICH10R
CPU INTEL CORE 2 DUO E8500 - 3.16 GHZ 1333 MHZ DUAL CORE BOX
MSI V146-09S GEFORCE N9800GT T2D512-OC PCIE 16X DX10 512MB
RAM Corsair XMS2 DDR2 2Gb (2x1Gb) PC6400C4DHX
HDD 500 gb sata2 western digital 7200rpm
TOPOWER M2 600W ATX 12V2.0 20+4 PINES BLACK
Antec Three Hundred Case
Samsung LN37A450 37" working @ 1360x768px through HDMI cable
Kubuntu 8.10 w/KDE 4.2 (beta)

Cheers,
Mguel

---

### Post by Morganman on 2009-01-23
Hi
In defence of the chipset I have a MSI F3 Neo motherboard which is P45 ICH10R based and have had a clean install of Ubuntu 8.10.

The only problems ive had have been as a result of my 'Newbie' inexperience.

---

### Post by Anubis on 2009-07-16
[http://ubuntuforums.org/showthread.php?p=7628737#post7628737](http://ubuntuforums.org/showthread.php?p=7628737#post7628737)

---

### Post by haider_up32 on 2009-08-15
i have had no problems with ASUS P5Q Pro on Linux. Sound and Atheros worked without drivers on 8.04 and 9.04 .

---

### Post by grafted_scion on 2009-10-13
Just got a P5QC everything except audio working out of the box.
[This forum link explains how to make the ALC1200 work.  :P]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

---

### Post by grafted_scion on 2009-10-19
> **grafted_scion said:**
> Just got a P5QC everything except audio working out of the box.
[This forum link explains how to make the ALC1200 work.  :P]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

Not entirely true i did get a error message during ubuntu boot
Got rid of the PCI: Bios Error by disabling Express Gate in BIOS.
Didn't mess much with Marvell IDE its disabled anyway as i don't have IDE hardware

Works great i am happy. :P

---

