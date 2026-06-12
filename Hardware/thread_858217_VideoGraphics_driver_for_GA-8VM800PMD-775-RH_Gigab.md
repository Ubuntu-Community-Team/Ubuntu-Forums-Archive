---
title: "Video/Graphics driver for GA-8VM800PMD-775-RH Gigabyte motherboard"
date: 2008-07-13
forum: Hardware
---

### Post by t-timmy on 2008-07-13
Hello,

I didn't find any post with [my motherboard]("http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=2333")'s serial number.
I am unable to go above 800x600 resolution, and there are no propriety drivers available.

Can anyone help please?

---

### Post by tech0007 on 2008-07-13
Try the openchrome driver.  'sudo dpkg -i xserver-xorg-video-openchrome'. Then edit your /etc/X11/xorg.conf to include 'openchrome' as 'Driver' under 'Devices' section.

---

### Post by t-timmy on 2008-07-13
> **tech0007 said:**
> Try the openchrome driver.  'sudo dpkg -i xserver-xorg-video-openchrome'. Then edit your /etc/X11/xorg.conf to include 'openchrome' as 'Driver' under 'Devices' section.

Sorry for being a little linux illiterate...

```
jonathan@cma-black:~$ sudo dpkg -i xserver-xorg-video-openchrome
[sudo] password for jonathan: 
dpkg: error processing xserver-xorg-video-openchrome (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xserver-xorg-video-openchrome

```

---

### Post by tech0007 on 2008-07-13
my bad...it should be:

sudo apt-get update
sudo apt-get install xserver-xorg-video-openchrome
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf

Add this line under Devices
Driver   openchrome

ctrl-O + [enter] to save
ctrl-X to exit
ctrl-alt-bclspace to restart X

---

### Post by t-timmy on 2008-07-13
OK, it's much better, thanks.
A couple of issues:
1) The login screen is huge in its resolution now - I can only see the Ubuntu logo and the textbox where I enter my username and password. Is there a way to fix that? (I tried hitting print screen to take a screenshot but it didn't work)
2) I still can't enable desktop effects... Is there a way I can do that?

---

### Post by tech0007 on 2008-07-13
1.  I'm not sure about the login screen issue. You can google for the resolution.

2.  Unichrome/Openchrome/Via graphics chipset does not support desktop effects atm.

---

### Post by t-timmy on 2009-01-18
Hi,

Sorry to revive this old thread, but I'm trying to perform the same actions but unable to go above 800x600 again.

My xorg.conf Device section is like this now:

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection

```

It used to be like this:

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

```

I also tried adding the line to the end of the section but still stuck @ 800x600, sometimes even only 640x480!

---

