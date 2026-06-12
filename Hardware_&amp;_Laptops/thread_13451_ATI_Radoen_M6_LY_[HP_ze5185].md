---
title: "ATI Radoen M6 LY [HP ze5185]"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by avorio on 2005-01-31
Hello!

I'm considering a migration [from Windows XP] to Ubuntu. :)

Does Ubuntu support the **ATI Radoen M6 LY** video card of my HP Pavilion ze5185 laptop?

-a

---

### Post by JoWilly on 2005-01-31
[QUOTE=avorio]Hello!

I'm considering a migration [from Windows XP] to Ubuntu. :)

Does Ubuntu support the **ATI Radoen M6 LY** video card of my HP Pavilion ze5185 laptop?

-a[/QUOTE]

Are you sure its called Radeon M6 LY ?

Because I have installed both (Warty and Hoary) on a Sony Waio Laptop with an Ati Mobility M6 LY card (don't know it is the same ?), a few days ago. Works fine.

If you want to make sure it works, you can try the Live CD.

---

### Post by daniels on 2005-01-31
All varieties of the M6 work just fine.

---

### Post by avorio on 2005-02-01
[QUOTE=daniels]All varieties of the M6 work just fine.[/QUOTE]
 Really?

It's because I installed Fedora Core 3 before and couldn't use it because the incompatibility between the ATI Mobility video card and X.org. Doesn't Ubuntu have the same issue?

-a

---

### Post by avorio on 2005-02-01
[QUOTE=avorio]It's because I installed Fedora Core 3 before and couldn't use it because the incompatibility between the ATI Mobility video card and X.org. Doesn't Ubuntu have the same issue?[/QUOTE]
Oh, well.. I just installed Ubuntu 4.10, did all the updates suggested, and now I'm getting the same error I was getting with Fedora Core 3. Suddenly, the screen freezes and doesn't come back anymore. Is this version already using X.org? Is there any way to use XFree instead?

-a

---

### Post by daniels on 2005-02-01
What error is this?  How do you trigger it?

---

### Post by avorio on 2005-02-01
[QUOTE=daniels]What error is this?  How do you trigger it?[/QUOTE]
 I can still move my mouse cursor, but the graphical interface stays freezed. I happens unexpectedly! I logged, GNOME was loaded and then I clicked the "Computer" item on the top panel. Just after the dropdown menu was opened the interface freezed.

-a

---

### Post by avorio on 2005-02-15
[QUOTE=daniels]What error is this?  How do you trigger it?[/QUOTE]
 Hey Daniel! Did you see my reply?

---

### Post by daniels on 2005-02-15
Weird; I'm not sure, sorry.

---

### Post by mahroon on 2005-10-08
hi its nice its work every were i love it please give me

---

### Post by avorio on 2005-10-08
[QUOTE=mahroon]hi its nice its work every were i love it please give me[/QUOTE]
What is it? Any moderator seeing this?

---

### Post by Kebabji on 2005-10-08
my m6 ly (ati radeon 9000 mobility) works fine *except* for 3d acceleration

---

### Post by ahillerin on 2005-10-18
I ve got the same card... I dont know if it is working for 3D but I have a problem by using the ati driver... I want a resolution of 1280*1024 

so I set the xorg.conf as this:

....
Section "Extensions"
    Option    "RENDER" "Enable"
EndSection
....

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"ati"
	Option		"AGPMode"        "4"
	Option  	"AGPSize"        "64"    #    default: 8
	Option  	"RingSize"        "8"
	Option 		"BufferSize"        "2"
	Option 		"EnablePageFlip"    "True"
	Option  	"EnableDepthMoves"    "True"
	Option 		"RenderAccel" "true"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x1024" "1024x768"
	EndSubSection
..
up to 		Depth		24
	
...


but all the time i have an error messages in the Xorg.0.log

(II) RADEON(0): PLL parameters: rf=2700 rd=60 min=12000 max=35000; xclk=16600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(WW) RADEON(0): Mode 1200x1024 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1040 1176 1344  768 770 776 806

I tried also with different parameter for vsync in the Monitor section but without success... 


Anybody already successed to have this resolution on such kind of card?

---

### Post by gustl87 on 2006-08-03
hi i got the same problem ... with a ati M6 on my compaq evo n410c.

most time it freezes when i'm using firefox - but most time i use firefox^^

the only thing i could do is to change from "ati" to "vesa" in the xorg.conf - and all the nice 3D support has gone.

and vesa makes also troubles, when you are running vmware. the fullscreen mode is unusable because of may stripes and other errors.

"radeon" and "fglrx" are not better than "ati" - freezing continues with "radeon" and with "fglrx" X is anable to start (but maybe i just habe to reconfigure ist).

will there be any fix the next time or is there any older driver/kernel available which runs stable ?

the video chip is not that new ... so it is funny, that suddenly there is a ug^^ or was there no working driver the time (3-4years) before ?

thx & good luck !

---

### Post by gustl87 on 2006-08-16
hello

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "radeon" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

