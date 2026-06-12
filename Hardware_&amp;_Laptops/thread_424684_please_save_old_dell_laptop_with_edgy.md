---
title: "please save old dell laptop with edgy"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by tonytux on 2007-04-26
I run Dapper on my desktop and my friend wants me to install an Ubuntu distro on his old Dell Latitude CPi A, so I downloaded the special boot params disk (only having 128M of Ram to work with).  And have been woking at it for hours, trying, failing and reseting, trying my dapper releases and nothing seems to work, I don't have a strong enough grasp on passing boot params to the kernal to know how to get around some of the possibale probles....please help:confused: :mad:
i've tried "exclude port 0x800-0x8ff", i've tried "aic7xxx-aic7xxx = =no_probe" I've tried "BOOT DEBUG =3" and am now trieng expert mode, I read somewhere that the server install might work first and to then install the desktop, waiting for cd to burn to try that.....

---

### Post by tonytux on 2007-04-27
](*,) :frown: well I think after the 12th attempt to install Ubuntu, the hard drive just went out.  I get this very "comforting" *click click, click click* coming from the drive, I tried to reboot and all that happy stuff but I still get "no drive deteted at IDE0" from the dell bios.  I guess there was no saving this thing. Now off to ebay or somthing for a new PCMCIA drive....:(

---

### Post by aysiu on 2007-04-27
I don't know anything about special boot parameters, but this will help you do the command-line install and add the desktop later:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Dilleyboy on 2007-04-27
Does the dell system still have the Pre-Boot System assements(PSA's)? <Fn>+<Power>?

---

### Post by tonytux on 2007-04-27
ok after a few hours of sleep I think I may have my head back in order.  The hard drive is now being identified, I guess I over heated it.  the spots that seem to get hung up in the install (of Feisty not Edgy) process is 1 loading the installer(keeps wanting to jump online to a mirror site, with but doesn't seem to recognize the USB cable modem), 2 error release file, no valid release file found 3 detecting and mount cd rom faild. and when I use the Dapper Cd I used to install my desktop I get caught every time at the loading hardware, even when I try to pass the "aic7xxx-aic7xxx=no_probe" or "exclude port 0x800-08ff".

My Feisty server has the same problem as the Feisty desktop install cd's (both of which are the alternate versions for under 256M Ram). Here are the few answers I get off of the bios

Dell Latitude CPi A300ST
CPU                   PII 300Mhz
Ram                   128M
Vid Mem             2.5M
Internal cache     256kb
HD                     12073M seen by Ubuntu partitioner as 12.1G
Bios revised in    1999 as V. A04

now I understand that the Gnome desktop requires a CPU of 400Mhz or more so I recently downloaded the XUbuntu Feisty and will be burning that, luckily this (Damn) Dell accepts CDRW's, I will try that barebones, but If I can't recognize the usb/cable internet connection I don't see being able to apt-get anything, This has no LAN, only a WPA card, with no wireless currently at my place here now.

---

### Post by tgalati4 on 2007-04-27
You might have better luck booting with "Ultimate Boot CD" and using a disk utility to rewrite the drive.  Chances are the drive is past due, but you may be able to add some life to it with a low-level format with the appropriate manufacturer's utility.

A PII at 300 MHz is minimalist for full-blown Dapper.  The real problem is 128 MB.  Unles you are using the Alternate CD, the normal installer will hang up after several minutes of loading files.  That has been my experience.  The way around it is to either use the alternate CD, or, add a generous swap disk, properly formated as Linux swap (type 83).  It's best to put it at the end of the disk, behind your boot and data partitions.  With a 12GB drive, you can afford a 500 MB to 1 GB swap partition.  This will also come in handy when you need to run the live CD because it will detect and mount the swap partition and make it run faster as well.

Alternatives to Ubuntu include DSL, Puppy Linux, Vector Linux, Slackware, and others that folks can attest to that will run well on that machine.  Xubuntu might be the best compromise, but then you can do a standard Debian Etch install and add whatever window manager you see fit.

Add smartmontools when you have finished your installation and check the disk drive's SMART capability.  At least you can check the number of hours on the drive and any recent read/write errors.

Good luck.

---

### Post by tonytux on 2007-04-27
I don't see any preboot system assesment any where within the bios and *fn power* only turns the laptop off, all other *fn* command is pretty self explanitory, 9 dig key pad, CRT LCD susspend, volume, etc...

---

### Post by tonytux on 2007-04-27
i have been using the alternate cd's, except for my dapper release, I do have a slackware V10 laying around, if I can't seem to get the xubuntu going I might try that,(waiting for it to burn now) and I'm still curious about the bare bones iso,(need burner free to burn that).

---

### Post by tonytux on 2007-04-27
The Dell was runing *Sindows* XP when I got it which recognized the usb/cable network right away, so I figued Ubuntu wouldn't be that hard to install with. is ther any Lx distro that recognizes this type of net config durring install. Or do I have to like get some minimalist installed and then use apt-get with an "upgrade" cd like xubuntu Feisty or something for this to pan out well?

oop there it goes, "Error reading Release file" durring the alternate Feisty attempt, could this be an .iso download error, or a burn error on my part, the cd/dvd creator doesn't give me a speed option when I write an .iso to disk...

---

### Post by tonytux on 2007-04-27
and the Xubuntu is ginving me the same release file error, "the cd rom does not seem to contain a valid release file, or that file could not be read correctly.  You may try to repeat cd-rom detection but, even if it does succeed the second time, you may experience problems later in the installation."  I never seem to get a valid release file read at all, going to the bare bones disk...

barebones doens't recognize the network (usb/cable modem) either.....off to slackware I guess,

where would I find smartmontools and how could I get it into a distro .iso?

---

### Post by tgalati4 on 2007-04-28
Have  you tried Damn Small Linux?  It's only 50MB and runs fast in 128 MB.  You can add apt-get then add a bunch of Debian-based tools.  If your CD reader is toast, then you can put it on a USB stick and boot off of a special floppy.  It's not a full-distro, but it does run well on older hardware.  I've had months of uptime on an old P1, 166MHz laptop with 64MB RAM.

---

### Post by K.Mandla on 2007-04-28
I used to have that exact same laptop, up until about a month ago. 

[http://ubuntuforums.org/showthread.php?t=394569](http://ubuntuforums.org/showthread.php?t=394569)

It should work fine. If you're getting CD errors, is there any chance that the drive is faulty, or the CD you burned? Honestly, mine ran start to finish without a single error. And you can do [amazing things]("http://kmandla.wordpress.com/2007/02/14/un-freaking-believeable/") with that laptop. So don't give up! :D

---

### Post by tonytux on 2007-04-28
well, after trying and trying, the HD finally gave out totally. Not many things left to do other than buy a new one.  I did get DSL and INSERT to both boot up fully.  Insert reveald LOTS of errors on the HD before it decided to completly die out. And with DSL I got a better feel of how behind this laptop is. And that my ACPI must be forced because of the age of the Bios. Which may have helped to confluster things in the installs I tried.

I found this funny because the desktop system I am currently running on right now, is an old 98 Gateway 400c, with only 128M of Ram, and I didn't get ANY problems loading in a full Dapper install, not even that ACPI thing,(nothing that poped out like this anyway, I'm sure it might be there), or limited ram issues.

Also with the DSL, I finally got some traffic out to my Cable modem connected via USB, but couldn't seem to get a full connection, just enough to see the USB light blink on the modem. No type of useable internet connection with that.  Anyways, when and if my budy lets me do a full install on his next hard drive you might see me back in here.  Just thought someone might want to hear the end of the story.

That "click click click" is not a good sound to hear from a hard driive, it's not the fault of a linux installation, but mearly that HD's time to go, and like the good people who have been doing this for a long time continue to say, back it up, back it up, back it up.

Thanx for the time and effort on everyone's part.

And K Mandla, thanx for that little bit of hope, my buddy will appreciate the vision of the last step in his laptops quest to be free and fun.

---

