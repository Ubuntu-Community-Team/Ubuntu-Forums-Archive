---
title: "1280x800 after nVidia driver install?"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by novaburst on 2005-03-18
I have a HP zd7000 15" Wide Screen laptop.

Before I installed the nVidia driver, Ubuntu allowed me to change my resolution to 1280x800.
After I installed the nVidia driver, I can only go to a max resolution of 1024x768.

Has anyone successfully gotten 1280x800 to work after the nVidia driver install?

This is driving me crazy. I have searched with Google all night and cannot find anything that helps.

---

### Post by acascianelli on 2005-03-18
have you tried just going into System>Preferences>Screen Resolutions?  if you have and you cannot see that resolution in there then try the following.

edit your /etc/X11/xorg.conf file.  towards the bottom youll see a Monitor section.  My laptop also has a widescreen display with the same resolution.  heres what mine looks like...

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
```

also down lower, there will be a Screen section similar to this...

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

---

### Post by novaburst on 2005-03-18
Thanks for the reply.
Mine looks pretty close to that.
When I go to Screen Resolutions, the maximum I can go is 1024x768

Here is part of my XF86Config-4
I am running Warty 4.10.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-64
	VertRefresh	43-60
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31M [GeForce FX Go 5600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

---

### Post by amerigo5 on 2005-03-18
You might want to try the following: 

Identifier "Generic Monitor"
HorizSync 30-107
VertRefresh 50-185
Option "DPMS"
Modeline "1280x800" 159.74 1280 1296 1552 1664 800 800 815 835
ModeLine "1680x1050" 214.51 1680 1800 1984 2288 1050 1051 1054 1103

Refer to the original post at 
[http://www.ubuntuforums.org/showthread.php?t=5464&highlight=50-185](http://www.ubuntuforums.org/showthread.php?t=5464&highlight=50-185)

---

### Post by novaburst on 2005-03-21
I tried it and it still doesn't make a difference.
My max resolution is still 1024x768.

I am at a stand still with this. I am not sure what to try now. It is extremely frustrating.
Could the problem be with my modeline? Could it be the vert or horiz values?

---

### Post by marvec on 2005-03-25
Try adding 
  Option "IgnoreEDID" "on"
to your device section. I had the same problem as you and xorg ignored the 1280x800 mode due to unsupporte hsync rate.
Here is the relevant part of my xorg.conf:
```
Section "Modes"
  Identifier "16:10"
  ModeLine "1280x800" 83.5 1280 1344 1480 1680 800 801 804 828
EndSection

Section "Monitor"
    Identifier  "Notysek Wide"
    HorizSync   30-90
    VertRefresh 50-90
    
    Option "DPMS" "on"
    Option "UseEditFreqs" "1"
    UseModes "16:10"
    Option "FlatPanelProperties" "Scaling=aspect-scaled"
EndSection

Section "Device"
    Identifier  "Notysek GeForce"
    Driver      "nvidia"
    Option      "NoLogo" "true"
    Option      "IgnoreEDID" "on"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Notysek GeForce"
    Monitor     "Notysek Wide"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x800"
        ViewPort    0 0
    EndSubsection
EndSection

```

---

### Post by novaburst on 2005-03-25
That worked!!
Thank you so much for the reply, I really appreciate it!

I knew it had something to do with the driver, because I used "nv" and I was able to use the 1280x800 resolution.

But now that I put the line in you told me about, I can use the "nvidia" driver and everything works fine.

Whoo hoo, you made my day!!
 :D

---

### Post by marvec on 2005-03-27
[QUOTE=novaburst]That worked!!
Thank you so much for the reply, I really appreciate it!

I knew it had something to do with the driver, because I used "nv" and I was able to use the 1280x800 resolution.

But now that I put the line in you told me about, I can use the "nvidia" driver and everything works fine.

Whoo hoo, you made my day!!
 :D[/QUOTE]

You are welcome! I solved that problem the same day. When searching for solution I found your question by fortune...

---

### Post by robalone2008 on 2008-05-28
thank you SO MUCH! i have never spent so long on one single problem! thanks!

---

