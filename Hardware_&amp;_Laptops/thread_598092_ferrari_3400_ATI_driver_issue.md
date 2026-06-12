---
title: "ferrari 3400 ATI driver issue?"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by jhellman on 2007-10-31
Hello,

I have some trouble setting up video driver for ATI card on Ferrari 3400.

This is the video controller version that this machine has eaten:

xxx@ferrari-ubuntu:~$ lspci -n | grep 0300
01:00.0 0300: 1002:4e50
xxx@ferrari-ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

I have just recently upgraded to 7.10 - I had the same trouble with 7.04 and 6.10.. In 6.10 I was able to get the beryl work for a while until I upgraded to 7.04.. In 7.04 I was able to configure the display to work decently (quite fast). However now after upgrading to 7.10 the screen is very s-l-o-w.

The sticker on the on the computer said that the controller should be "ATI Radeon Mobility 9700", however the check above shows a slightly different version..

When I try to open "Ati Catalyst controil center", I get an error message "there was an error initializing Catalyst control linux edition.  It could be caused by following: No ATI graphics driver is installed or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware or configure using aticonfig"

right - obviously a screwed up system.. Anyone with same situation and hints how to get to working state.. I have tried browsing the different instructions but no resolution yet - only blank screen every now and then or no change at all..

---

### Post by overdrank on 2007-11-01
> **jhellman said:**
> Hello,

I have some trouble setting up video driver for ATI card on Ferrari 3400.

This is the video controller version that this machine has eaten:

xxx@ferrari-ubuntu:~$ lspci -n | grep 0300
01:00.0 0300: 1002:4e50
xxx@ferrari-ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

I have just recently upgraded to 7.10 - I had the same trouble with 7.04 and 6.10.. In 6.10 I was able to get the beryl work for a while until I upgraded to 7.04.. In 7.04 I was able to configure the display to work decently (quite fast). However now after upgrading to 7.10 the screen is very s-l-o-w.

The sticker on the on the computer said that the controller should be "ATI Radeon Mobility 9700", however the check above shows a slightly different version..

When I try to open "Ati Catalyst controil center", I get an error message "there was an error initializing Catalyst control linux edition.  It could be caused by following: No ATI graphics driver is installed or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware or configure using aticonfig"

right - obviously a screwed up system.. Anyone with same situation and hints how to get to working state.. I have tried browsing the different instructions but no resolution yet - only blank screen every now and then or no change at all..

Hi have you enabled the restricted drivers and then search synaptic for xorg-driver-fglrx. This is what I used on a ATI 9600. Now if your system has low memory if might seem sluggish. Then change your driver in the xorg to fglrx. Backup your xorg first
To copy Xorg
[Code]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then to edit your xorg
```
gksudo gedit /etc/X11/xorg.conf
```

Good luck!

---

### Post by jhellman on 2007-11-02
Hi,

thanks for advice - no resolution yet thought. The xorg-driver-fglrx was installed.. and the xorg.conf file is as follows:

--

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

---

this laptop has 2 GB of main memory, so I do not think that is the issue either.. Any ideas what should be done to reconfigure xorg.conf?

---

