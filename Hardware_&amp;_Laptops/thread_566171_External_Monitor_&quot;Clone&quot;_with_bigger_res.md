---
title: "External Monitor &quot;Clone&quot; with bigger resolution?!"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by fahim on 2007-10-03
Hello,

I got a X60 Tablet with the max. resolution of 1024x768. And I got a 22" Widescreen LCD Screen with max. 1680x1050.

I want to use both Displays in Clone Modus, but after setting the clone modus, my external monitor will keep the same resolution as on my laptop. Is there any possibility to get my external monitor to 1680x1050?

Thank you very much

---

### Post by fahim on 2007-10-05
Nobody has an idea?

---

### Post by MaximusTG on 2007-10-05
If you want to use clone mode, you are limited to the maximum resolution of the smallest display. In your case, 1024x768. 
So in order to help you, what do you want to do with it? Do you want to use 1 screen at a time, so use the big screen when laptop is "docked" and use laptop screen when on the move?
Or do you want to extend your desktop to the big monitor?

I myself have a 19" 1440x900 monitor that I use with my laptop. I installed Gutsy beta because of this, because Gutsy has a more recent xserver-xorg , which includes xrandr 1.2. With that you can easily switch between displays on the fly. 
What I have now in my setup:
An xrandr script that will switch between laptop (1280x800) and monitor (1440x900) bound to a function key. and in my xorg.conf I have included modes "1440x900" and "1280x800". If I boot with the monitor attached, it uses 1440x900 and show a portion of that on the laptop (but since I have it closed, this doesn't matter) if I boot without monitor it seems like X detects that the laptop screen doesn't support 1440x900, so uses 1280x800.

I am not an expert in this, but this works for me.
Some handy links:

[http://burtonini.com/blog/computers/randr-2007-02-06-17-50](http://burtonini.com/blog/computers/randr-2007-02-06-17-50)
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950)

and the relevant portion of my xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"	
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x800"
		Virtual		1440 1440
	EndSubSection
EndSection

```

---

### Post by fahim on 2007-10-05
Thank you your xorg.conf works great with my external monitor.

So now I can see on the external with 1680x1050 and on the lcd of my laptop I can see a part of the big resolution. Do you know how I can now turn off my lcd from my laptop if an external lcd is attached? When I close my laptop, both lcd screens will turn off...

---

### Post by MaximusTG on 2007-10-06
Well, the fact that the screens turn off you can change in the power manager settings 
(There you can specify what your system should do when you close the lid)
I took the xrandr script from one of the links that I gave you, changed it to my situation, and put it in the list of startup programs. That way, regardless of xorg settings, my screens are always set correctly.
That's probably not the most "neat" solution, but unless someone can teach me how to do this better (automatically changing settings on basis of connected output devices)

---

