---
title: "Fujitsu-Siemens Amilo M1425"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by houksi on 2005-04-13
Hi!

I've tried few times to get my laptop work with dualboot but no success. Is here anyone who have succeeded. The errors what I have encountered are:
- just blank screen, no boot and
- lilo shows just L and stuck!
- grub just says "... loading" and stuck!

I would like my laptop work with dualboot ;) 

Yes, first partition is Windows 20GB, second is 20GB is for backup and rest were unpartitioned. I tried Grub too but no success tho :( With my previous laptop there weren't any problems but my new shiny one have :D

Interesting issues to add:
- Windows XP install disk or Rescue CD wont boot correctly unless the hard disk is unpartitioned.
- It looks like MBR don't take bootloader after first installation...

---

### Post by erkki70 on 2005-04-13
Terve!
Do you have Windows installed in the 1st partition already? How many partitions do you have? Anything yet on? Did you do anything special during install? IMHO Grub is a little more user friendly and does a good job for dual boot usually...
Give more details so people here can help you.

Cheers,
Erkki

---

### Post by houksi on 2005-05-11
Anyone succeeded with Amilo M1425 and Ubuntu? My Desktop computer runs fine, but my laptop is still mysterio  :roll:  so all information is needed!

Sincerely

Desperate ;)

---

### Post by pau on 2005-05-12
Hi...

this is very strange, because I do have the SAME laptop and it's working flawlessly for me.

Only the wlan configuration thing is putting me on my nerves and the screen save mode, when I close the laptop it goes like in hibernate but then instead of resuming it reboots

But the rest of things is working perfectly...

Maybe your CD copy is dammaged. But don't give up.

I deleted the window$ partition... All linux

---

### Post by houksi on 2005-05-12
Well that is something good to hear it runs 100% Ubuntu :D but not 50% MS and 50% Ubuntu...

Gonna try with new harddisk :)

---

### Post by J D Wijbenga on 2005-05-12
I have the same laptop and both Hoary and Warty work well. Even Wireless was automaticly installed. Alle I had to do was enter my connetcion information. 

So far the speedbuttons and sleep do not work.

I also find the fan of my laptop starting very often and being very loud. Even when the processor worklaod is only around 3%.

Good luck with getting yours to work.

JD

---

### Post by XneoX on 2006-08-13
Hi I got the exact same laptop the amilo 1425.
1.8 G, 512 Ram, 60 GIG, ATI 9700 128 mb graphics , DVD RW+/-.. :cool: 

I first had intsalled Windows on NTFS with aroound 20 GB. and had another FAT partition of 25 GIGs (acts as a common drive between the two OS). Then I installed the Ubuntu 5.10 Breezy because I had the CD's on me. I created a Rieser FS partition as my Boot partition and left around 900 or so mb for SWAP at the end of the drive. During installaion it asked me for the GRUB loader for my XP installed on the other drive. And I jsut went on with it.

It had problems with the display driver and it used a generic display driver. Without modifying it anyway, I just upgraded it to the 6.06 Dapper version (Check the site for details on how to upgrade).
With the upgrade, I got the drivers for video card, and all my problems were solved except for the memory Card slot. I cannot figure out how to use that.
The laptop works just smooth !! No hassles at all except for as "pau" said configuring the wireless for diffferent networks everytime i shift, is a kind of a hassle. Even the sleep, hibernate and the "quite" (the button which brings down the speed of the fan and quitens the laptop a bit) works perfectly and so do all the other quick launch shortcut buttons, volume control,mute , brightness control keys .
Try doing the installaion in this way, it worked perfectly for me.

---

### Post by mikka303 on 2006-08-28
Hi there,

Ive just installed ubuntu in my Amilo M1425 and everything works perfectly except the screenresolution, i cant to setup to resolution higher than 1024x768, ive read lots of forums and faqs and i just cant get the monitor range. Can you guys please help me out?

Thanks in advance,


Miguel

---

### Post by XneoX on 2006-08-29
Ma screen resolution was recognized during installation and it took 1280x800 as default. I used the Ubuntu 5.10 Breezy to Install. Even that detected it perfectly.. An then I upgraded to the 6.06 Dapper which again gave me no problems.
The only thing that doesnot work is the Card Reader/Writer. Anyone got that to work ??

---

### Post by florizs on 2006-09-02
> **mikka303 said:**
> Hi there,

Ive just installed ubuntu in my Amilo M1425 and everything works perfectly except the screenresolution, i cant to setup to resolution higher than 1024x768, ive read lots of forums and faqs and i just cant get the monitor range. Can you guys please help me out?

Thanks in advance,


Miguel

Hi Miguel,
The sollution is quite simple, you need to enter the new screen resolution in /etc/X11/xorg.conf
since I'm working on a windows machine now I can't describe all the steps.

open a terminal
type sudo gedit /etc/X11/xorg.conf
you have opened the graphics configuration files.
there is a section there (screen) in which there are a couple of screen modes entered like this: 24 "800 x 600"  "1024 x 786" etc..
you need to add in the same style your screen resolution eg, "1280x800" for the widescreen amilo 1425.

if you have any configuration questions message me about it.
good luck!

correction: i've booted linux now your xorg.conf screen section should look like this:
```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

