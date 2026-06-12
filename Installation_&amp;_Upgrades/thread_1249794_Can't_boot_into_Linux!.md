---
title: "Can't boot into Linux!"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by knightbringer on 2009-08-25
Sorry so long...

I am having some trouble installing ubuntu 9.04.  First I made a 50GB FAT 32 primary partition on my HD that also has Win XP MCE 2005 and Server 2008 dual booting (I have server on my HD because I am in school right now trying to learn networking and wanted to practice on Server 2008 before I took the class).  So far, so good, but when I try to install Ubuntu from Windows onto the 50GB FAT32 partition, it takes 3 hours just to get to the 25% mark on installation and then appears to just freeze.

So I figured that I would try to just use a Linux live CD and just boot from the CD-ROM into a linux environment and mess with it there (even though it is supposedly slower).  It seems that nothing would boot from the CD/DVD-ROM drive despite changing the settings in BIOS and the boot load sequence.  The computer doesn't even "try" to boot from the CD/DVD-ROM drive.  It just goes straight to the black screen where I choose to launch Server 2008 or Win XP MCE 2005.  I figured maybe the Server 2008 that I had installed on my HD was messing things up...

So then (since I have a 2nd HD I'm not even using) I decided to just install Ubuntu onto an empty HD.  I wiped the 2nd HD blank and then disconnected the SATA connecter from the 1st HD (the one with Win XP... and Server 2008 on it) and just connected that SATA connector to the 2nd HD (empty HD) so the mobo would see it as the primary HD (aka the only HD).  That way I would have a "clean" computer with just the hardware and an empty HD.

I then tried to boot with the Ubuntu 9.04 installation disk to try and install it onto the HD and it gave me an error of "insert System Disk" or something like that.  I then tried my Windows XP MCE 2005 and that works.  It actually starts trying to install Win XP MCE 2005.  So I guess that my CD/DVD-ROM can boot, but for some reason it won't recognize the Ubuntu installation Disk (or any boot disk except MS for that matter as I've tried GPart, MEMTEST86, etc).

I've checked the MD5 hashes for the Ubuntu installation iso and there is no corruption in either downloading or burning the file.  I wanted to use Memtest86 to check my RAM to see if there was an issue there, but as I stated before... it appears that I can't boot anything from my CD/DVD-ROM drive unless it is WIN XP MCE 2005 or Server 2008.  :confused:

It doesn't make any sense to me.

I don't know if anyone else has had problems like this, but it is frustrating to say the least.  I have been trying to figure this out for a couple days now and any help would be greatly appreciated.  Thank you.


Here are the specs for my computer:

Processor: am2 x2 6000
              
              -Motherboard: GIGABYTE GA-M57SLI-S4
              -Case: APEVIA X-QPACK2 Aluminum
              -Case Fan: RCTIC COOLING Arctic Fan 12L
              -Power supply: A-Power 500W
              -Memory: Kingston DDR2-800 2GB
              -Hard drive: 500GB SATA 7200 RPM 16MB
              -Optical drive: 20X LightScribe SATA DVDRW
              -Floppy drive: Please include 1.44mb 3.5inch
              -Video card: GeForce 8600GT 512MB 2DVI
              -2nd video card: GeForce 8600GT 512MB 2DVI
              -TV tuner card: Hauppauge WinTV-HVR 1800
              -Sound card: onboard
              -Networking: onboard
              -Media reader: 21-1 media card reader

---

### Post by louieb on 2009-08-25
> **knightbringer said:**
> The computer doesn't even "try" to boot from the CD/DVD-ROM drive...I then tried to boot with the Ubuntu 9.04 installation disk to try and install it onto the HD and it gave me an error of "insert System Disk" or something like that. 

Sounds like you burned it as a data CD when you should burn as a  CD image.

Browse the CD in windows - you should see files and folders. If all you see is 1 large file then you need to burn the iso file to CD as an image.  [BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto")

---

