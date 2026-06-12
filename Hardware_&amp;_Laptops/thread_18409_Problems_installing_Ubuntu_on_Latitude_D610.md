---
title: "Problems installing Ubuntu on Latitude D610"
date: 2005-03-06
forum: Hardware &amp; Laptops
---

### Post by evisboy on 2005-03-06
I am having major problems installing Ubuntu on the new Dell Latitude D610. Ubuntu is not recognizing my hard drive. After the initial boot-up from the install disk, I go through the hardware discovery, but I never get the option to automatically configure my drive. I only have the Manually Partition Disk option. When I choose that option, I get several options, but none showing my partition table. 

This is an odd problem, because the Slackware installation went fine. 

My hardware is as follows: 

Pentium M 730 (1.6Ghz), SXGA Display (the new Sonoma chipset)
Radeon X300 Video 
60GB 5400 RPM Hard drive
512 mb DDR2
Intel Pro Wireless 2200 
CD burner

Has anybody installed ubuntu on the D610? 

I tried the live cd to no avail. THe Knoppix live cd also did not work. THe problem for both live cds was a black screen after boot. 

This is an odd problem, and I have yet to find any sufficient information from my searches.


Anybody have any idea, clue, experience in this particular thing?

---

### Post by eternity on 2005-03-07
[QUOTE=evisboy]I am having major problems installing Ubuntu on the new Dell Latitude D610. Ubuntu is not recognizing my hard drive. After the initial boot-up from the install disk, I go through the hardware discovery, but I never get the option to automatically configure my drive. I only have the Manually Partition Disk option. When I choose that option, I get several options, but none showing my partition table. 

This is an odd problem, because the Slackware installation went fine. 

My hardware is as follows: 

Pentium M 730 (1.6Ghz), SXGA Display (the new Sonoma chipset)
Radeon X300 Video 
60GB 5400 RPM Hard drive
512 mb DDR2
Intel Pro Wireless 2200 
CD burner

Has anybody installed ubuntu on the D610? 

I tried the live cd to no avail. THe Knoppix live cd also did not work. THe problem for both live cds was a black screen after boot. 

This is an odd problem, and I have yet to find any sufficient information from my searches.


Anybody have any idea, clue, experience in this particular thing?[/QUOTE]

I have the D610 too, and gor into the same problem, harddrive was not detected. D610 uses SATA and my guess is that SATA driver is missing in Warty. It's a little odd tough, Warty livecd dected my hdd but not the installation cd.

I installed Hoary 5.04 array 6 instead and it worked right out of the box.

---

### Post by evisboy on 2005-03-07
Thanks for the tip. I will check that out. 

One question, when you were using the warty live cd, was your screen blacking out after the initial boot-up, or did it work fine for you?

---

### Post by eternity on 2005-03-07
[QUOTE=evisboy]Thanks for the tip. I will check that out. 

One question, when you were using the warty live cd, was your screen blacking out after the initial boot-up, or did it work fine for you?[/QUOTE]

All went fine when i used warty livecd, except for the screen resolution. No blank screens and the ATI chipset was detected. It's odd that we are getting different results since my configuration is very similar to yours:

1,86ghz
ATI Radeon X300, SXGA
1024mb Dual-DDR
80gb hdd
IPW2200

You might wanna try out Hoary livecd as well.

If you ever get the X300 card to work with the ATI proprietary Xorg driver, let me know how you did it :)

---

### Post by evisboy on 2005-03-11
I just tried the Hoary LIve CD and it is not detecting my cd rom. I cannot get the model # for the drive, and Dell apparently doesn't know it either, which I find baffling. 

I do think it's a Philips, based on the serial # starting with PH

Any ideas?

---

### Post by lyly on 2005-03-11
I also have this computer, and I saw this problem with hoary array 5. With daily buils (9 March) I could install it and my cd-rom was well detected...

I also have problem with screen resolution (1280x768 as I should have 1400x1050) if you have any clue let me know about it...

My config is:
Pentium M 1.6GHz
512Mb Ram
Intel 915GMA graphic chipset
SXGA display
NEC CD/DVD-RW

Lynda

---

### Post by draconas on 2005-03-17
I just installed Warty on my 610 last night. Had no problems during installation but it isn't seeing my sound card :(

---

### Post by Martin2610 on 2005-03-22
Hi all,

I'm trying to get 3D Support for my D610 for two days. But I guess there is no driver thats supports 3d on X300. ATI says , they are not responsible, because driver for mobile devices are provided by the notebook facturer. And Dell is not offering any driver. So I guess we have to live without 3D support or find another way. To be true, I don't see any ...

see ya

Martin

---

### Post by SDNick484 on 2005-03-27
I've been running Fedora Core 3 on my D610 for about a month now; if anyone wants my .config file, I'd be happy to post it (ought to resolve the HDD, CD, and video card issues -- well at least get you a useable radeon driver not the fglrx one).

---

### Post by Tymon on 2005-03-28
Hey! Join the club! [http://www.ubuntuforums.org/showthread.php?t=18807&highlight=sata+installation](http://www.ubuntuforums.org/showthread.php?t=18807&highlight=sata+installation)

Hope they'll fix the SATA issues soon.

---

### Post by kyouens on 2005-03-29
I'm running the Hoary nightly build on my new D610 and most everything is working, with the exception of the @#$ 3D of course.  The fglrx package info says that the x300 is supported. . . .hmm.

---

### Post by eternity on 2005-04-01
Regarding the X300 I found this thread on gentoo forums:

[http://forums.gentoo.org/viewtopic-t-312143.html](http://forums.gentoo.org/viewtopic-t-312143.html)

Atleast it gives a little more detailed information about the problem...

---

### Post by Chindastulfo on 2005-04-11
[QUOTE=eternity]I have the D610 too, and gor into the same problem, harddrive was not detected. D610 uses SATA and my guess is that SATA driver is missing in Warty. It's a little odd tough, Warty livecd dected my hdd but not the installation cd.

I installed Hoary 5.04 array 6 instead and it worked right out of the box.[/QUOTE]

I had many problems with my new AMD64 PC (SATA drive) when trying to install several linux flavours , until I included a parameter in the boot installation prompt. Please read the help info on the boot screen for I am not sure of the exact word (it changes according the the distro selected).

You can try this : "linux noapic" (without quotes, of course)

Then the hard drive was detected and the intall did not freezed at all.

Good luck!

---

### Post by cirnath on 2005-04-12
[QUOTE=evisboy]I am having major problems installing Ubuntu on the new Dell Latitude D610. Ubuntu is not recognizing my hard drive. After the initial boot-up from the install disk, I go through the hardware discovery, but I never get the option to automatically configure my drive. I only have the Manually Partition Disk option. When I choose that option, I get several options, but none showing my partition table. 

This is an odd problem, because the Slackware installation went fine. 

My hardware is as follows: 

Pentium M 730 (1.6Ghz), SXGA Display (the new Sonoma chipset)
Radeon X300 Video 
60GB 5400 RPM Hard drive
512 mb DDR2
Intel Pro Wireless 2200 
CD burner

Has anybody installed ubuntu on the D610? 

I tried the live cd to no avail. THe Knoppix live cd also did not work. THe problem for both live cds was a black screen after boot. 

This is an odd problem, and I have yet to find any sufficient information from my searches.


Anybody have any idea, clue, experience in this particular thing?[/QUOTE]


Saw your post while looking for tips on sound problems in kde with the 610.  I ran into the SATA/HD problem today with the 2005.1 SR1 release of Ark Linux.  Turns out the PCI ID in the hwdata package points at the SATA RAID driver ahci, which doesn't know how to handle the non-raid config.  Normal config requires the ata_piix driver.  Had to update the pcitable, modprobe.conf, then generate a new initrd.. but otherwise it seems to be in business now.. aside from the bleepin sound.

---

