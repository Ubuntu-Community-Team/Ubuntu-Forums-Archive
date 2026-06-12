---
title: "fglrx X server crash on logout"
date: 2009-02-18
forum: Hardware
---

### Post by fedoraboy on 2009-02-18
This is driving me nuts.  I've filed a bug report, but if anyone can help me sort out what's going on, I'd be forever thankful.

What's Happening:  everything seems normal... but when I log out, X crashes and the entire system hangs hard.  After that, the only choice is the power button.  No ctrl-alt-backspace.  No ctrl-alt-pfkey.  No ssh over network.  Dead.

What I've got:
hardware:HP Pavillion dv7 family
adapter: 01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
driver: latest catalyst 9.1 from ATI, built according to the ["unofficial wiki"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

my Xorg.log doesn't have a lot of useful error info:
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x65) [0x480f35]
1: /lib/libc.so.6 [0x7f26ea2360a0]
Saw signal 11.  Server aborting.

Replacing the fglrx driver with ati driver -- it works but the graphics are awfully slow.  I get better graphics on my 10 year old nvidia card.  :)

There seems to be lots of iterations of this problem over the years that vary by distribution, graphics card, etc.  I feel like I've tried every iteration of workaround in all of them..... and no  joy.

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by nedyar on 2009-03-09
I have the same problem, nobody have the solution?

---

### Post by GMWeezel on 2009-03-10
BUMP: This is driving me crazy as well. Toshiba Satellite L305D Series.

---

### Post by niskel on 2009-03-13
I'm having the same problem with:

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

---

### Post by notoriousdbp on 2009-03-16
Me too with a Radeon HD3200 on 8.10 64-bit with Catalyst 9.2.  Can't logout or switch user.  Got 9.1 running on OpenSuse and that's all fine

---

### Post by notoriousdbp on 2009-03-17
Anyone?

---

### Post by nedyar on 2009-04-01
I have the same problem with radeon hd 3470 on a fujitsu siemens amilo Pa 3553 and ati catalyst 9.3 installed on Ubuntu 8.10 64 bit

---

### Post by dreamsR4living on 2009-08-03
> What's Happening: everything seems normal... but when I log out, X crashes and the entire system hangs hard. After that, the only choice is the power button. No ctrl-alt-backspace. No ctrl-alt-pfkey. No ssh over network. Dead.

I am having the same problem, but I use a Nvidia 8500GT videocard. I am on 9.04.

Included xorg.conf

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by zecorvina on 2009-11-12
I have the same problem and already identified that the cause is the ati proprietary driver, I know there is a new version on the ati site, but I am afraid to corrupt my system if I try it. Can someone try it on a non-work pc and post the result?

---

### Post by fedoraboy on 2009-11-12
Anyone that has this problem on <9.10 tried the 9.10 restricted drivers?

I've booted this laptop with the 9.10 live cd and it seems to work... but you can't really turn up the built-in restricted drivers on the live cd... as that requires a reboot... which takes you back to the standard live image.

If I ever get off my lazy *** on the weekend, I'll try it on my home laptop.

---

### Post by notoriousdbp on 2009-11-13
Fixed for me in 9.10 - which is a beautiful upgrade I might add

---

### Post by moh980 on 2009-11-14
i have the same problem with Ubuntu 9.10 (clean install) and Toshiba Satellite L510


any help? please

---

### Post by zecorvina on 2009-12-04
> **notoriousdbp said:**
> Fixed for me in 9.10 - which is a beautiful upgrade I might add

But... do you have a ATI graphics card? I have been seraching  for a solution for this bug since I upgraded to 9.10 on a Sony Vaio VGN-FW51JF. Nobody seems to have the faintest idea on how to solve the bug. 

This bug appears with ATI Radeon Card and Ubuntu 9.10 with the ATI lattest drivers. 

Searching in detail, I found that when you logout the atieventsd.sh searches for a GDM auth file in a directory where it does not exist (and I could not find it anywhere else), and fails crashing badly.

I think this shoud be fairly easy for an expert user to solve. Or post a more technical review which could lead to the correction of this anoying bug.

Thank you

---

