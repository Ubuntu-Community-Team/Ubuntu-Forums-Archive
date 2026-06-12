---
title: "Problems at 1280x1024"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by JaF on 2005-05-20
I have a 19" TFT which works fine a 1280x1024 in Windows. However, If I select 1280x1024 in ubuntu the image looks all distorted. Does anyone know why this might be?

Here is my /etc/X11/xorg.conf
```

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"LL-T19D1-H"
	Option		"DPMS"
	HorizSync	32-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"LL-T19D1-H"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


```

Thanks in Advance

---

### Post by Zelut on 2005-05-20
You may need to find the correct refresh rate to adjust it to.  You'll need your monitor make, model, etc.  Try to google search to find the correct refresh rate for your model & give that a try.

Be careful however.  Don't just guess on a refresh rate & try something out.  You can damage hardware if you put in a refresh rate that is not in its normal range.

---

### Post by jonrkc on 2005-05-20
[QUOTE=kuyaedz]You may need to find the correct refresh rate to adjust it to.  You'll need your monitor make, model, etc.  Try to google search to find the correct refresh rate for your model & give that a try.

Be careful however.  Don't just guess on a refresh rate & try something out.  You can damage hardware if you put in a refresh rate that is not in its normal range.[/QUOTE]
 You might try running xvidtune and tweaking the settings that way, to see what the result will be.  Using xvidtune I was able to get a "modeline" that I inserted into my xorg.conf file that exactly centered the image on the screen; before that, it was several millimeters off to the right, even when the built-in "auto-adjust" on the monitor was used.  

I also inserted a line "DisplaySize" in the "Section 'Monitor'" portion of xorg.conf, following a suggestion I read some time ago.  I got the exact display size from the booklet that came with the monitor (a Princeton VL1916 20-inch LCD).  The result of these changes in my file:

```


Section "Monitor"
        Identifier      "VL 1916"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
        DisplaySize     376.3 301       
   ModeLine "1280x1024"   108.00   1280 1332 1444 1688   1024 1025 1028 1066 +hs
ync +vsync


```


When I was using Mandrake/Mandriva Linux 10.1, I was able to get a better xorg.conf file by using xorgconfig, and got a sharper display that way.  But trying it under ubuntu resulted in not being able to start X.  I had saved the xorg.conf that I knew worked, so I was able to restore it and get back into X.  

But xvidtune works for me with ubuntu.

---

### Post by JaF on 2005-05-20
[QUOTE=kuyaedz]You may need to find the correct refresh rate to adjust it to.  You'll need your monitor make, model, etc.  Try to google search to find the correct refresh rate for your model & give that a try.[/QUOTE]
That was the first thing I tried and it hasn't changed things at all:(

[QUOTE=jonrkc]You might try running xvidtune and tweaking the settings that way, to see what the result will be.  Using xvidtune I was able to get a "modeline" that I inserted into my xorg.conf file that exactly centered the image on the screen; before that, it was several millimeters off to the right, even when the built-in "auto-adjust" on the monitor was used.[/QUOTE]
The problem is the screen is so scrambled it is impossible to see what is going on.

EDIT:

Here is a photo of the desktop top at 1024x768:
[IMG]http://www.joefarish.co.uk/images/res/1024.jpg[/IMG] 
This is what I get at 1280x1024:
[IMG]http://www.joefarish.co.uk/images/res/1280.jpg[/IMG]

---

### Post by nad on 2005-05-20
man i810 for information specific to your video driver (there are known issues).

You may 'tab' through your configured resolutions with the key sequence: Ctrl->Alt->(number pad) - or +

If you have damaged your xorg.conf file, you may need to do a: dpkg-reconfigure xserver-xorg at a recovery mode terminal prompt to get a usable display.

---

### Post by JaF on 2005-05-20
[QUOTE=nad]You may 'tab' through your configured resolutions with the key sequence: Ctrl->Alt->(number pad) - or +[/QUOTE]
That only lets me change between 1024x786,800x600 and 640x480.

[QUOTE=nad]If you have damaged your xorg.conf file, you may need to do a: dpkg-reconfigure xserver-xorg at a recovery mode terminal prompt to get a usable display.[/QUOTE]
I have already tried that and that is what has produced this configuration. It's fine for resolutions <= 1024 but it doesn't work at 1280 :(

---

### Post by nad on 2005-05-20
man i810

1280 x 1024 may not be seen as a valid resolution. You may wish to decrease your display depth to see if it becomes available.

---

### Post by JaF on 2005-05-20
[QUOTE=nad]man i810

1280 x 1024 may not be seen as a valid resolution. You may wish to decrease your display depth to see if it becomes available.[/QUOTE]
Hmmm it doesn't say that in my man pages  ](*,) . But I guess its just not possible for now.

---

### Post by jonrkc on 2005-05-20
[QUOTE=JaF]Hmmm it doesn't say that it my man pages  ](*,) . But I guess its just not possible for now.[/QUOTE]
 ```


DESCRIPTION
       i810  is  an  Xorg  driver for Intel integrated graphics chipsets.  The
       driver supports depths 8, 15, 16 and 24.  All  visual  types  are  sup&#8208;
       ported  in  depth  8.  For the i810/i815 other depths support the True&#8208;
       Color and DirectColor visuals.  For the 830M and later, only the  True&#8208;
       Color  visual  is supported for depths greater than 8.  The driver sup&#8208;
       ports hardware accelerated 3D via the Direct  Rendering  Infrastructure
       (DRI),  but only in depth 16 for the i810/i815 and depths 16 and 24 for
       the 830M and later.

```

Above is what I found in man i810--it certainly does look as though depth might be the problem.  Hmm.  I would try decreasing depth to see if that solves it--I wouldn't like to have to settle for such a solution, though...

---

### Post by nad on 2005-05-20
For the third time; man i810.

Judging by the screenshots you have just posted, 1280x1024 does work. The 'scrambling' you didn't decscribe appears to be a font or memory problem. The memory issue can be handled by options listed in the man page. Try different configurations to find one that works best for you.

---

