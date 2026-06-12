---
title: "Getting dual monitors to work in Ubuntu 64"
date: 2008-05-27
forum: Hardware
---

### Post by tronovan on 2008-05-27
Hello all, I am using Ubuntu 64 bit edition.  I am trying to get my **ATI Radeon HD 2400 pro **video card working with two monitors.  I have this working fine in Windows XP but after many tries, I have never been able to get this working under linux.    I downloaded the drivers directly from the ATI website and I make sure I'm getting the 64 bit version.  I install the drivers and run Catalyst control center to configure the displays. 
 
```
amdcccle
```

When I run this, I have the option to use clone mode or big desktop mode. By default, I am in clone mode where both my monitors display the same thing.  When I choose to use Big Desktop mode, I am prompted to restart.  When I restart, one monitor shows (out of range) and the other monitor is in an extremely low resolution setting as I cannot even see the field for my username and password.

Next, I use **CTRL ALT +** and **CTRL ALT –** to change the resolution so I can see what I’m doing.  When I do this, the desktop is too big to fit on the screen.  When I move my mouse to the edge of the screen, the entire desktop scrolls.  Although I now have a bigger desktop, both screens show the same thing.  I am still unable to get the dual monitors working the way they do in Windows XP.

Does anyone know a workaround or fix?

Thanks
--Donovan

---

### Post by tronovan on 2008-06-01
I've been able to resolve the dual monitor problem.  I'm posting this here just in case anyone else encounters the same issue.

I simply installed fglrx-control.

```
sudo apt-get install fglrx-control
```

During installation, I was asked several questions and I choose the defaults for everything.  After rebooting,  The dual monitors work with Big-Desktop mode.:guitar:

The only problem is that I don't think I'm using any type of hardware acceleration.  When I move windows, or scroll down a webpage, I notice an extreme lag or 'tearing.'  Here is my /etc/X11/xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Can anyone help me enable hardware acceleration on my card?

Thank

--Donovan

---

