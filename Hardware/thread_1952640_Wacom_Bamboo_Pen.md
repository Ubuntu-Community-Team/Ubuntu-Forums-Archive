---
title: "Wacom Bamboo Pen"
date: 2012-04-04
forum: Hardware
---

### Post by asearle on 2012-04-04
Hi Everyone,

I had a rather old Wacom pen-pad and it worked perfectly with no need to install software:  I just plugged it in and it was detected just like a mouse.  That was perfectly adequate for me.

This week I needed to replace this and so bought a Wacom Bamboo Pen which is a very basic unit ... but I only need basic functionality.

Unfortunately it does not seem to be detected by my Ubuntu which is 10.04 64bit.

As it is, I have (successfully) installed xserver-xorg-input-wacom, wacom-dkms and mypaint but the pad is still not detected.

I tried following this thread ...

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

... which seemed to supply comprehensive instructions but, despite an apparently successful installation, the pad was still not detected (I believe) and ...

lsmod | grep wacom 

... returned nothing.  And I am not sure which other diagnostics/checks I can should do.

There are many Wacom HOWTOs out there and people seem to have got the Bamboo Pen working.  But I feel swamped by information and am unclear/uncertain about both installation and diagnostics.

I also tried with "GIMP" and looked at the various input device settings hoping to find "Wacom" there too.  But this was not the case.

Anyway, I do hope that someone can help me move this forward?  I was so hoping that it would be a simple thing.

Many thanks for any tips and/or links that you can give,

Regards,
Alan Searle

---

### Post by Favux on 2012-04-04
Hi Alan,

My guess is you have a Bamboo Connect (Pen).  Post the output of *lsusb* in a terminal if you need that confirmed.  That's a third generation BambooPT and support for it is not yet in input-wacom.  That's part I. of the BambooPT HOW TO you linked to.  So if you did that that's why it didn't work.  Instead you have to patch input-wacom before you compile it.  See appendix 2 for the instructions.

---

### Post by asearle on 2012-04-05
Many thanks for this advice.  I will check the appendix 2 ...

alan@hp6910p500gb:~$ lsusb
Bus 007 Device 002: ID 056a:00dd Wacom Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alan@hp6910p500gb:~$

---

### Post by Favux on 2012-04-05
Yes, that's the Connect.
```
Third Generation models (released October 2011):
Bamboo Connect (Pen)			stylus 			
   (CTL470/K; Product ID = 0xdd)
```

---

### Post by asearle on 2012-04-05
Sorry to ask again but ...

The steps in Appendix 2 seem clear but the command ...

./configure --prefix=/usr

... returned messages that components were not found ...

checking for X11... no
configure: error: Package requirements (x11 xi xrandr xinerama) were not met:

No package 'xrandr' found
No package 'xinerama' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

... so I looked in synaptic and could not find xrandr or xinerama.

Are these components separate things that I need to install?  Or can I get this working by adjusting PATH variables as recommended by the script?

This is at the limit of my Linux knowledge so and short tips would really help me.

Many thanks,
Alan Searle

PS: I am running Ubuntu 10.04, 64bit.

---

### Post by Favux on 2012-04-05
Hi Alan,

Those look to be the development libraries or dependencies you need to install for the compile.  They should have been taken care of by the line:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
```
The line extends to the right out of sight.  Did you get the whole thing?  Also for 10.04 you need to install xorg-macros v. 1.8 (part II. b)).

---

### Post by engla on 2012-04-15
Did you try to load the wacom driver manually?

"sudo modprobe wacom"

---

### Post by asearle on 2013-01-27
I found that by upgrading to a more current version of Ubuntu the system was able to automatically recognise the tablet.

So the moral of the story is to not delay upgrading.

Regards,
Alan Searle

---

