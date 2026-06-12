---
title: "HP Pavilion dv6-3131tx laptop rendered unusable after installing ati drivers"
date: 2010-12-29
forum: Hardware
---

### Post by IrishAdam on 2010-12-29
Hi folks,

My mum just got back from Australia with a new HP laptop.

[http://h10010.www1.hp.com/wwpc/au/en/ho/WF06b/321957-321957-3329744-64354-64354-4247579-4344629.html](http://h10010.www1.hp.com/wwpc/au/en/ho/WF06b/321957-321957-3329744-64354-64354-4247579-4344629.html) 

First thing she said to me was "Can you get rid of that windows rubbish and put Ubuntu on it please" ( I have her well trained :) )

I tried 10.10 first but the right click didn't work so I decided to install 10.04 LTS. Everything went well and I updated the system.

The only issue is that the fan seems to run very fast and that side of the laptop was very hot. So hot that i cant even hold my hand on the video out D connector. So I decide to try the proprietary ATI drivers to see if it would fix the problem.

Now I just get a black screen after grub and the same happens when I try recovery mode.

I tried the xforcevesa command in the grub entry but no joy. The only bit of info i have is the if i press the power button at the black screen, The ubuntu logo appears with the dots under it and the dots are animated but nothing happens.

Any help would be great.

Adam

---

### Post by IrishAdam on 2010-12-30
It does appear that other people are having problems with ati switchable graphics cards on laptops, also known as hybrid graphics. The nice solution is the disable the low power card in the bios but unfortunately most hp machines don't have the option, mine included.

I haven't seen anyone describe the overheating problems that i am having with the open source drivers though. 

Is there any more info I can gather to help someone diagnose my issue?

---

### Post by Vengenz on 2011-01-06
+1

I have the same computer and the same problem

---

### Post by honewatson on 2011-01-20
Try this tutorial:

[http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html](http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html)

Make sure you have 10.10 with /sys/kernel/debug/vgaswitcheroo/switch installed.

---

### Post by ptrinder64 on 2011-01-20
I'm not sure if I can really help with the graphics problem - running an HP DV6 (not sure if it is the same model - guessing not though as mine is second hand) using the fglrx drivers and not having too many issues with them. 

If you think it may be the same graphics card (mine is an ATI Mobility Radeon 4200 series) then you could try booting using a live CD, making a copy of your current xorg.conf and then seeing if yours differs too much from this one:

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

If you change it and it doesn't work, just revert to the original.

As per the overheating, I in fact have the same problem but slightly different. I bought my laptop in the UK and have brought it with me to Brazil. Whereas it operated fine in the UK it is overheating a lot here. I therefore bought a laptop cooling pad from somewhere like [http://www.ebuyer.com/](http://www.ebuyer.com/) and this helped a lot. Secondly, I downloaded Jupiter from Synaptic which helped me monitor the heat and keep it to a minimum.

---

### Post by IrishAdam on 2011-01-31
Thanks everyone for your help.

I installed 10.10 again and got the right click going using this guide 

[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)

I have applied the patch suggested by honewatson and will see if it fixes my overheating problem.

I will let you know how I get on.

Adam

---

### Post by IrishAdam on 2011-02-07
Just a quick note to let you know that my overheating problems have been solved. Thank you everyone for the help.

---

