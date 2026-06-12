---
title: "MSI Wind Top AP1941"
date: 2012-08-03
forum: Hardware
---

### Post by Ektor-5 on 2012-08-03
Hi all,

I have installed Ubuntu 12.04 LTS on two MSI Wind Top AP1941, equipped with touchscreen and Atom processor, here are the specs:

```

CPU 			Intel® Cedar Trail D2500 Processor
OS 			gFree DOS
Chipset 		Intel NM10 Express
Memory 			DDR2 2GB Max: 4GB
Graphics 		Integrated Intel® GMA 3600
Panel Resolution 	18.5" 1366x768
Touch Panel 		Single-Touch
HDD 			3.5” SATAII 500GB
Optical 		Drive 	Tray-in DVD Super Multi
Audio 			2 x 3W Speaker
LAN 			10/100/1000
Wireless LAN 		802.11 b/g/n
```

But there is some issues:

 - Ubuntu is using default vesa/fbdev graphic driver
 - Resolution is locked on 1024x768
 - Touch screen isn't calibrated properly

HOW TO RESOLVE:

**Graphic/Resolution issue:**

I followed the guide on 
[http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/) , but I used only this commands.

```
# Just add the repository http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/ to your APT:
sudo add-apt-repository ppa:sarvatt/cedarview

# Install the add-apt-key utility
sudo apt-get install add-apt-key

# Install the Repository KE
sudo add-apt-key 0x4c96de60854c4636

# Make apt-get update
sudo apt-get update

# if you're using PAE kernel, remove it and install generic kernel
sudo apt-get install linux-headers-generic linux-image-generic
sudo apt-get remove linux-headers-generic-pae linux-image-generic-pae

# Install the cedarview drivers
sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers

# Reboot the System
# sudo reboot
```

**Touchscreen issue**:

I installed xinput-calibrator via apt

```
sudo apt-get install xinput-calibrator
```

I opened a terminal and launched it, but specifing the device (it may not be "13" for you, check with `xinput`):

```
xinput-calibrator --device 13
```

Then I copied the output and pasted it on /etc/X11/xorg.conf.d/99-calibration.conf, launching:

```
sudo gedit /etc/X11/xorg.conf.d/99-calibration.conf
```

If you are lazy to install the calibration tool, just paste this:

```
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"IDEACO  IDC 6681"
	Option	"Calibration"	"1072 7073 1780 6565"
EndSection

```



I hope that this can help someone.
If someone else have issues on this pc please post here!

---

### Post by migueli2 on 2013-02-13
Hi!

Thanks for the steps.
I managed to make it work "Graphic/Resolution issue" that u posted.
But i fail in the "Touchscreen issue" and it's the most important for me to make it work.

installed correctly sudo apt-get install xinput-calibrator
But fails in the next step, when i type xinput-calibrator --device 13 shows me the error:

command not found

Any ideias to help me out ? 


Thanks

---

