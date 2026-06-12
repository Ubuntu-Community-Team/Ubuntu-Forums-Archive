---
title: "Ubuntu 9.04 clean install - max resolution is only 800x600"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by mingle on 2009-04-26
Hi,

After a clean install of 9.04 on my Compaq Evo 510 SFF desktop (intel 82845G gfx) I seem to be stuck with a generic VESA GFX driver (I'm assuming) that only allows 800x600 as the maximum screen resoltuion.

When I ran Ubuntu 9.04 from the LiveCD the resolution was okay, at my preferred 1024x768, but after the clean hard disk install, all I can select is either 800x600 or 640x480.

In the preferences->display util, it also says my monitor is type "Unknown"

In 8.04 I was able to use displayconfig-gtk to select the correct GFX driver and scree, but there doesn't appear to be an equivalent in 9.04...

Any ideas?

Cheers,

Mike.

---

### Post by cariboo on 2009-04-26
There have been regressions in the intel drivers, have a look at his [thread=1130582]thread[/thread].

---

### Post by mingle on 2009-04-26
Hi,

Thanks for the reply...

I'm afraid that possible solution is a bit beyond my abilities!

Oh well, it's back to XP for the foreseeable future!

Cheers,

Mike.

---

### Post by Garrovick on 2009-04-26
Compatibility with hardware is a Linux Achilles heel. The computer I have with a nvidia integrated 6100 simply did not work above 800X600.  When a friend gave me an old 6200 card, Linux graphics worked at 1400X900, even without installing a driver.

iPods are the same way, it's why I've kept, and will keep XP on my netbook.

---

### Post by lotech on 2009-04-26
You are not alone mingle, IMO what prevents Linux to become main stream on desktop is the problem it has in handling graphical interface, partly due to the vendors refuse to provide support to it. I am using ATI and always have problem setting the screen resolution, so does my Philips LCD it never get detected properly, but beside that Linux is lot better than Windows, it just take some getting use to and your patient....

---

### Post by Seks on 2009-04-26
> **Garrovick said:**
> 
iPods are the same way, it's why I've kept, and will keep XP on my netbook.

What? Ever since NBR was released netbook compatibility has become a strong point for Ubuntu. Unless you use some very obscure brand, you could most likely expect everything to work. I use 9.04 on my eee and it runs fast and flawlessly, and so did 8.10 (w/array kernel).

---

### Post by Garrovick on 2009-04-26
> **Seks said:**
> What? Ever since NBR was released netbook compatibility has become a strong point for Ubuntu. Unless you use some very obscure brand, you could most likely expect everything to work. I use 9.04 on my eee and it runs fast and flawlessly, and so did 8.10 (w/array kernel).

IPods/iPhones/iTunes do work with Ubuntu. Ubuntu does with my Aspire One, (and by the way so does OSX), but not iPods and Ubuntu. No matter which computer it's installed on. The same problems crop up constantly about many other hardware problems in these forums.

Like I said, it's a the Achilles heel of Linux, which is going to keep Linux third in line after OSX and Windows.

Other than this mp3 player/hardware issue, Ubuntu works as well as the other two.

---

### Post by mingle on 2009-04-26
@Garrovick & lotech,

I know what you mean...

It's a real pity...

Windows just works on, and with, pretty much everything, plus I've never have any issues regarding stability and/or malware...

Maybe they're sort it out with a later release? maybe I'll give it another go then...

Cheers,

Mike.

---

### Post by TjankMjaster on 2009-04-26
Evening.  New to the forums here,... Since you mentions Ipods and Itunes,.. Anyone have experience using WINE to run I-tunes,... any issues?   any other threads you can direct me to?

Cheers, P

---

### Post by sunilnair21 on 2009-04-27
Hi Mingle,

first backup your xconfig file i.e (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

then edit the file using vim (vi /etc/X11/xorg.conf

Under the Screen Section add this line in the last DefaultDepth  24

open a subsection like below

SubSection "Display"
    Depth   24
    Modes   "1024x768"
  EndSubSection
Logout from XServer and login back see if this helps

Regards
Sunil

---

### Post by joseba on 2009-04-27
thx sunilnair21, that worked for me.
ubuntu 9.04 Jaunty...
fujitsu siemens amilo Mini ui3520
display 9"
i change resolution to 1024x600
reboot
and ok

un saludo!
juanjoa

---

### Post by peakshysteria on 2009-04-27
> **TjankMjaster said:**
> Evening.  New to the forums here,... Since you mentions Ipods and Itunes,.. Anyone have experience using WINE to run I-tunes,... any issues?   any other threads you can direct me to?

Cheers, P

Ipod works nicely for me.Using Rhythmbox and Songbird instead of Itunes.

Here'sa few pics of my Intrepid setup of Songbird;

[http://bildr.no/image/289698.jpeg](http://bildr.no/image/289698.jpeg)


[http://bildr.no/view/289694](http://bildr.no/view/289694)

---

### Post by mingle on 2009-05-03
Hi Sunil,

My xorg.conf seems to be pretty empty (which is the same as when I installed 8.10 months ago). Does this look correct?

I've added the lines you suggested in the screens section. But after a reboot, it made no differnce...

Here it is:

----------

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
SubSection "Display"
	Depth 24
	Modes "1024x768"
EndSubSection
EndSection

---------

Cheers,

Mike.

---

### Post by mingle on 2009-05-05
Hi,

I found the problem - something I was not really aware of:

I had the monitor connected to the PC via a KVM switch, which was obviously somehow causing issues identifying the correct monitor/driver...

I just connected the monitor directly to my Linux PC and did a clean install and it now looks fine!

To say I'm happy is an understatement!

Cheers,

Mike.

---

