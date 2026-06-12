---
title: "Laptop resolution"
date: 2009-06-02
forum: Hardware
---

### Post by Locke on 2009-06-02
I have a IBM Thinkpad R51, the native resolution of this laptop is 1024x768, it is so horribly annoying to run at the resolution because everything is so large, i was wondering if there is any way i can force a higher resolution to be displayed on my screen?

---

### Post by brianfactors on 2009-06-02
I don't know much about IBMs at all, or about your specific config. Here's just a couple leads:

1) Your Xorg is where you could go. Edit /etc/X11/xorg.conf and find where it sets you resolution. Might allow you to manually set it.

2) This could definitely create problems if your graphics card doesn't support it. Have you searched for your graphics card to see if there's a driver from the manufacturer or elsewheres?

To find out about your hardware, you can type lspci into a terminal.

Hope this helps you get started in the right direction.

---

### Post by LepeKaname on 2009-06-02
Edit your /etc/X11/xorg.conf:

```
Section "Monitor"
    Identifier    "LCD"
#    HorizSync      28-78         I'm not sure about this value 
#    VertRefresh    50-75         I'm not sure about this value 
EndSection

Modifica los valores de acuerdo a tu monitor

Section "Screen"
    Identifier    "myscreen"
    Device        "Intel Extreme Graphics 2"
    Monitor        "LCD"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Device"
    Identifier "Intel Extreme Graphics 2"
    Driver "i810"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"myscreen"
EndSection
```

This is a very basic config file. You must check first HorizSync and VertRefresh for your monitor as they can fry your screen if they are set incorrectly. Follow the links I posted here and try to figure out which is the best setup for you.

Cause your laptop has a "Intel Extreme Graphics 2" you will be interested in these links:

[http://ubuntuforums.org/showthread.php?t=5963](http://ubuntuforums.org/showthread.php?t=5963)

[http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2](http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2)

[http://www.mat.ucm.es/~oub/thinkpad/](http://www.mat.ucm.es/~oub/thinkpad/)

Good Luck!

---

