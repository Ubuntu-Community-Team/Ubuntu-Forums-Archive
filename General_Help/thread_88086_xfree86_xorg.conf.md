---
title: "xfree86 xorg.conf"
date: 2005-11-09
forum: General Help
---

### Post by jhonijim on 2005-11-09
i have the configuration settings for my monitor its a sony gdm-20d10 but its in a format for xfree86 and i need to know what ineed to do to make it work with xorg.conf the text is as followes:
> Section "Monitor"
	Identifier	"Sony GDM-20D10"
	HorizSync	40-82
	VertRefresh	50-180
	Option		"DPMS"

        Modeline "gdm_1600x1200" 162 1600 1664 1856 2160 1200 1201 1204 1250 +HSync +VSync
        Modeline "gdm_1280x1024" 80 1280 1312 1456 1712 1024 1027 1030 1064
        ModeLine "gdm_1152x864" 105 1152 1192 1352 1440 864 865 875 895
        Modeline "gdm_1024x768" 110 1024 1056 1184 1360 768 770 774 805
        Modeline "gdm_800x600" 65 800 816 880 1048 600 600 603 631 +hsync +vsync
        Modeline "gdm_640x480" 50 640 648 696 832 480 481 484 509 +hsync +vsync
        Modeline "gdm_720x600" 55 720 728 776 912 600 600 603 631 +hsync +vsync
        Modeline "gdm_720x540" 55 720 728 776 912 540 541 544 569 +hsync +vsync
EndSection



---

### Post by Joh_ on 2005-11-09
Xorg.conf uses the same configuration from what I know.

---

### Post by Dr. Nick on 2005-11-09
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

thats what mine is like for my monitor. Seems alot different. What are you trying to fix with this?

---

### Post by Joh_ on 2005-11-09
His configuration handles mostly refresh rates at different resolutions.

I only have the Identifier and Option "DPMS" in my configuration. It figured out the refresh rates itself :p

---

### Post by Romzhv on 2005-11-10
I had kida the same problem with my Samsung LCD (193P). It keeped showing me only 60Hz at 1280x1024. Here what I did to fix it:
1. Installed proper drivers for my ATI Radeon video.
2. Went to manufacturers web site and wrote down all frequencies (Horizontal,Vertical,other settings) and **preferred resolution too**.
3. Got rid of all low-bit and small-number-of-pixels resolutions (They were not needed anyway).
4. Edited xorg.conf so that X is using the one and only **preferred resolution**, recommended by manufacturer (but of course, with my special ajustments).

Everything is working fine so far.:smile:

---

### Post by jhonijim on 2005-11-10
i got this monitor for free and it is off a sun workstation its a 20 inch monitor with a trinitron tube but it needs a spicefic range of a refressh rates and resolutions if it helps my video is a nvidia riva tnt2 model 64 i had to adapt the 13w3 plug on the monitor to the hd15 on my vid card but it wont auto detect the monitor settings because of the adapter

---

### Post by Dr. Nick on 2005-11-10
So you know the model number and the max refresh rate and resoulition?

What may be easier is to just rerun > sudo dpkg-reconfigure xserver-xorg and dont use auto detect, Once you reach the section on monitors use the advaced option, or the one above it and pick the correct max res and refresh rates. You wil have to go through the keyboard mess to get to it though. That should write the correct xorg.conf file for you

That may help some. I am not really sure I understand the type of the monitor and what you are trying to accomplish. My monitor stays at the same refresh no matter the resoulition so I may be missing something.

---

