---
title: "I upgraded to Jaunty - What can I do with my ATI x850?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-04-25
Ok I've got a problem as well.  I didn't read the information about the problems with upgrading to Jaunty and using an unsupported video card - I have an ATI x850, as noted in my signature, and I foolishly upgraded to Jaunty, had no video problems except the screen blinked once in a while.  I figured a re-install of the ATI driver would surely fix the problem (sorry - newb moment)

I keep copies of the ATI drivers in my /root directory so I used the uninstall script to remove the ATI driver and I rebooted.  I got the low-graphics screen of death which would result in a loss of signal to my monitor for each option that I selected.  I can't re-install the 9.3 driver because it is not compatible with Jaunty.  I can't install the 9.4 driver (with Jaunty support) because I have a card that is no longer supported.

So what can I do to get my machine running again other than clean install?  I have my /home directory on a separate partition but I've gone like a year and a half without reinstalling and I'd like to keep the streak going.  As many times as I preach to newbs to make a backup image, I don't have one - poo on me.  Is there some way I can set my xorg.conf to use the x850?

---

### Post by MaindotC on 2009-04-27
Bump - come on I've helped people enough that I deserve some help too.  How do I get the open-source ATI driver working from the command prompt?

---

### Post by Niniel on 2009-04-27
Uhm, that is really a funny attitude you're showing here...

Anyway, I don't know how to fix your issue, but I can tell you that I have an X800 card and I upgraded and don't have any problems. I am not using any proprietary drivers anymore, however, even though I did have the Catalyst driver before. So it seems the OS driver is good enough now at least for normal display purposes. And by that I mean that I can't enable desktop effects, but that never worked for me (strangely enough, it's not a problem at all on my notebook with a mobility Radeon 9xxx).

Here's my xorg.conf, maybe that'll help you:

> Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	BusID		"PCI:1:0:0"
	Driver	"ati"
EndSection

---

### Post by StuartN on 2009-04-27
> **strAlan said:**
> Bump - come on I've helped people enough that I deserve some help too.  How do I get the open-source ATI driver working from the command prompt?

You need to purge all the stuff that is currently installed and then install xserver-xorg-driver-ati - this is a metadriver that will select the right open source driver for your card. There is a detailed how-to (which possibly has 8.10 specifics) here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by MaindotC on 2009-04-27
Thank you for your replies and I wasn't showing any funny attitude.  Put yourself in my position - I've helped a lot of people but typically when I start a post no one replies and I'm very good about providing output to help others help me.  I made a mistake by upgrading and I don't think you should hint at any type of attiude I'm giving.  Thank you again for your replies and I'll see if they work and report.

---

### Post by MaindotC on 2009-04-28
I'm back into my graphical desktop - which is callged gdm right? - and the video is having some issues like some games have wierd/odd coloured shapes but I'm back in the desktop.  Thank you both for your help.

I'm reading the [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) that it will hopefully guide me in properly configuring my video card so I can continue using graphics-intensive applications without problems as I did in Hardy - unless you suggest I read elsewhere.

---

### Post by Niniel on 2009-04-29
Good to hear you had some success. So what did you do? Just followed that guide?

Btw, thanks for posting it. I added a few things in my own xorg.conf and now have desktop effects. Not sure yet if I really want them, but they are working.

---

### Post by MaindotC on 2009-04-29
Yeah I just followed that guide.  I followed the instructions to remove and purge fglrx but if I do a "locate" there are still loads of files that contain fglrx.  The monitor still blinks every 5 minutes and I have no video-out to my TV.  I may just get a newer, supported video card if I can't figure out how to configure the driver.

---

