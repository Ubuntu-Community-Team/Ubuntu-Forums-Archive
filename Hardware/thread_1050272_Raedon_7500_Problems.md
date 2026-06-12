---
title: "Raedon 7500 Problems"
date: 2009-01-25
forum: Hardware
---

### Post by rwfnetworking on 2009-01-25
I'm new to Ubuntu and have 8.10 running on a IBM Think Pad T42. I'm having issues with displays running slow, especially noticeable on the Internet where my web browser will take about 10 seconds to start displaying a page, but download speed is just fine. I noticed that while in Low Resolution mode that these problems went away. Can anyone recommend a driver that will work? Below is some info that should be helpful:

lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]

/etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Any ideas that may help?


Robert

---

### Post by gijoe3k on 2009-02-12
This thread may help you out. I was having problems with accelrated graphics until I followed what this guy did. Now things are flying:

[http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

---

