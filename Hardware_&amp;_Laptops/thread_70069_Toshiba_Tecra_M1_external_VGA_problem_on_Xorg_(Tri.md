---
title: "Toshiba Tecra M1 external VGA problem on Xorg (Trident XP4m32)"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by khiraly on 2005-09-28
Hi!
By typing FN-F5 compination the laptop switch to the external VGA port.
The problem is, that the resolution is still 1024x768 and cant be set to 1280x1024 (what my external (philips 190B) LCD monitor has).
I tried gnome-display-properties to switch the resolution.
In my /var/log/Xorg.0.log :
(II) TRIDENT(0): Removing mode (1280x1024) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1280x1024" (unknown reason)
The built-in laptop's monitor resolution is 1024x768. But how can I let know the Xorg server that I have an external monitor with a higher resolution?
My hardware:
Toshiba Tecra M1
Trident Microsystems CyberBlade XP4m32 (rev 91)
I use the Xorg builtin "trident" driver. 
I tried the vesa driver too, but I had only 4 color on my display (nearly impossible to read anything)
The interesting part from my xorg.conf:
Subsection "Display"
Depth    24
Modes   "1280x1024" "1024x768"
EndSubSection
Any ideas?
Best regards, 
Khiraly

---

### Post by mlomker on 2005-09-28
It does that even if you boot up with the monitor attached and the output going to it?

It might be possible to use modelines and disable the dri features (autodetecting screen capabilities).  Here's one of the [old-style]("http://www.resistive.net/XF86Config-4") files.  It's not easy, though...I've only gotten that to work properly on a couple machines.  Unfortunately, the commands are different for every monitor and video driver combination...

---

### Post by khiraly on 2005-09-29
[QUOTE=mlomker]It does that even if you boot up with the monitor attached and the output going to it?
[/quote]
It does not change anything
> 
It might be possible to use modelines and disable the dri features (autodetecting screen capabilities).

I have disabled dri. I have inserted two modeline line. But the error is the same.
I have put online the xorg.conf and the Xorg log file:
[http://khiraly.4242.hu/tmp/Xorg.0.log](http://khiraly.4242.hu/tmp/Xorg.0.log)
[http://khiraly.4242.hu/tmp/xorg.conf](http://khiraly.4242.hu/tmp/xorg.conf)
How can I disable autodetecting the monitors?
Khiraly

---

### Post by mlomker on 2005-09-29
> How can I disable autodetecting the monitors?


I don't know.  Google found other people with the same problem but I didn't find any solutions.  Have you verified that your machine has the latest system BIOS that is available?  The screen information is relayed through the BIOS.

---

### Post by khiraly on 2005-09-29
[QUOTE=mlomker]I don't know.  Google found other people with the same problem but I didn't find any solutions.  Have you verified that your machine has the latest system BIOS that is available?  The screen information is relayed through the BIOS.[/QUOTE]
I have begun the software installation with BIOS upgrading from toshiba.com
So I have now ACPI BIOS version 1.4 (I have bought the notebook with 1.3 BIOS)

Didnt found anything relating external vga in the bios.

---

### Post by khiraly on 2005-09-30
Finally I have successfully installed vesa driver and now work like a charm.
I can scroll the webpages is not slow anymore.

Finally we can focus on the external VGA adapter problem.

1. As I have a laptop there is no Ctrl-Alt-- and Ctrl-Alt-+ working. I dont have numpad. How can I change the resolution in Xorg? (is it a command for that?)

2. I tried to use gnome-display-properties. I can change the resolution to 1280x1024 but my monitor cant display it, there is an error message (builtin error message in my monitor):
> 
Image cannot be displayed. Please change to 1280x1024@60Hz the video input

(sorry, that I cant remember exactly the phrase)

3. Even I wrote modelines for my monitor, the X not seem to recognize those modelines. It use always the built-in vesa modes (11b).

4. How can I specify which vesa mode to use for my display?
There is 3 mode for 1280x1024:
11b
11a
119

My Xorg always pick up the **11b** mode. How can I change this behaviour?
I think the **119** vesa mode would be ideal for me.

The external monitor work with the 1024x768 resolution, but its not her native resolution (so the image is not sharp). The external VGA adapter seems to work, the problem that Xorg 1280x124@75Hz want to display (11b vesa mode), and the monitor only support 1280x1024@60Hz.

Can somebody help me? I think VESA driver is really current.

Khiraly

---

### Post by khiraly on 2005-09-30
If I try to ste manually the modelines, I got this message from the /var/log/Xorg.0.log:
(II) VESA(0): Not using mode "1280x1024_vesa" (no mode of this name)

The xorg.conf:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
ModeLine "1280x1024_vesa" 108.0 1280 1328 1440 1688   1024 1025 1028 1066 +hsync +vsync
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024_vesa"
        EndSubSection
EndSection

```

Any help would be really appreciate.

Khiraly

---

### Post by khiraly on 2005-09-30
[QUOTE=khiraly]The external VGA adapter seems to work, the problem that Xorg 1280x124@75Hz want to display (11b vesa mode), and the monitor only support 1280x1024@60Hz.
[/QUOTE]

Is not correct. I dont know which refresh rate is on external vga adapter.
On my desktop pc (gf2 mx400) I have 1280x1024@75Hz (indicated on the osd screen (on the monitor)). So Im now pretty sure, that my monitor support 1280x1024@75Hz resolution. How can I see, which refresh rate is on the external vga adapter?

Khiraly

---

