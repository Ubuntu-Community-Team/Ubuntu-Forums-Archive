---
title: "Resolution problem"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by mateamargo on 2006-10-14
I'm reading this [How To](http://ubuntuforums.org/showthread.php?t=83973), but I'm not able to make my monitor works in 1280x960 at 75 Hz. It's a Samsung 796MB.

Searching in Google I could see this info:
```

Horizontal refresh rate: 30-71
Vertical refresh rate: 50-160

```

I have added this info to **xorg.conf**, but I can only do a 1024x768 at 75 Hz.

So, I have used the Modeline Tool, but after adding those lines the option "1280x960" in "System/Preferences/Screen resolution" it's gone.

Any help?

---

### Post by John.Michael.Kane on 2006-10-14
In your xorg.conf find **Section "Monitor"** this mode line should work.

 Modeline "1280x960_75.00"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync

You should have something that looks like this

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       
    VertRefresh     
    Option         "DPMS"
    Modeline "1280x960_75.00"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync


Next Find this Section Next:

Section "Screen" 
------->Modes      "1280x960_75.00" this to SubSection     "Display" 

so it looks like this
SubSection     "Display"
        Depth       16
        Modes      "1280x960_75.00"

---

### Post by mateamargo on 2006-10-15
Well, now I have the option "1280x960" again, but only shows me 60Hz.

This is my xorg.conf in those sections:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
	# V-freq: 75.00 Hz  // h-freq: 75.39 KHz
	# Modeline "1280x960" 138.17  1280 1352 1520 1832   960  960  963 1005 
	Modeline "1280x960_75.00" 129.86 1280 1368 1504 1728 960 961 964 1002 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960_75.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960_75.00" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

It is anything wrong?

---

### Post by John.Michael.Kane on 2006-10-15
You need to copy paste this.
"1280x960_75.00" 

To this section over write the Org line that is in bold

SubSection "Display"
		Depth		1
		Modes		"1280x1024" **"1280x960"** "1024x768" "800x600" "640x480"

You should now have a line that looks like this.

SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960_75.00" "1024x768" "800x600" "640x480"

---

### Post by mateamargo on 2006-10-16
I don't know what's wrong. I just added what you told me but only let me choose "60 hz" in "1280x960"

---

### Post by John.Michael.Kane on 2006-10-16
Try changing the DefaultDepth	24 to 16

also this should read

SubSection "Display"
		Depth		16

---

### Post by mateamargo on 2006-10-16
I have solved this by installing the graphic driver correctly (following the Ubuntu guide).

Now it's working 1280x960 at 75Hz.

Thank you very much for your help.

---

