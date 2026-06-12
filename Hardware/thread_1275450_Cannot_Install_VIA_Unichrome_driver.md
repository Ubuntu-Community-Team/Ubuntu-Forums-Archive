---
title: "Cannot Install VIA Unichrome driver"
date: 2009-09-25
forum: Hardware
---

### Post by guv999 on 2009-09-25
hi
I identified that the unichrome driver was not fully installed in my system.  I went to openchrome.org, and they verified that this was due to my motherboard not being recognised and sorted that issue out.  
They advised me to go here and follow the instructions to complete installation:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

I have got as far as step 3 and can go no further:

**Edit the X server configuration file and cannot go further**.
It suggests that when I go to
gksudo gedit /etc/X11/xorg.conf
I will see a section marked 'Driver' that I shold change to 'openchrome'
What appears on my screen is:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

No mention of drivers at all.
As an alternative it suggests I could use:
sudo dpkg-reconfigure -phigh xserver-xorg
and select openchrome when asked.   When I enter this command all that is returned is:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090926011320

at this point I do not know what to do to get the driver installed and any help is appreciated.  Thank you

---

