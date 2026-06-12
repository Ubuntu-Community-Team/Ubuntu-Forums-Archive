---
title: "[SOLVED] ATI Radeon Mobility M6 LY no dri, Progress??"
date: 2008-09-06
forum: General Help
---

### Post by Alan Coleman on 2008-09-06
I did a google search for my graphics card ATI Radeon Mobility M6 LY 
and found alot of confused reports of partial successes and failures.
I wonder if anyone has desktop effects running smoothly on this card.
I would like to here from anyone who is using this card and what there
thoughts are on the desktop effects.

---

### Post by k40nflux on 2008-09-14
im interested as well, i have this card on my IBM thinkpad r32 and right now glxgears gives me a max of 45FPS and its painful to use this setup. i namely want the 3d to run kiba-dock. i could care less about having the cube.

---

### Post by inigomontoya on 2008-09-14
I've gotten this card to run successfully and smoothly using the open source xorg ATI driver.  Depending the available video ram (I had only 16mb) you may have to run it in 16 bit color to obtain the native resolution.

set this in your xorg.conf
```

Driver "radeon"
Option "AGPSize" "32"
Option "XAANoOffscreenPixmaps" "on"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "DisableGLXRootClipping" "on"
Option "AddARGBGLXVisuals" "on"
Option "AllowGLXWithComposite" "on"
Option "EnablePageFlip" "on"

```

I know for certain that you will at least need the AGPSize option.

More information in this post: [http://ge.ubuntuforums.com/showthread.php?t=899178](http://ge.ubuntuforums.com/showthread.php?t=899178)

---

### Post by Alan Coleman on 2008-09-22
I've gotten this card to run successfully and smoothly using the open source xorg ATI driver. Depending the available video ram (I had only 16mb) you may have to run it in 16 bit color to obtain the native resolution.


Hi followed the howto. Went very smothly on this Ibm X31 laptop, but still very bumpy running it. the screen may go black until its clicked on, other side effects. 

How do I find out my Video ram?
and how would I change to 16 bit couler native resolution


regards alan C

---

### Post by inigomontoya on 2008-09-22
> **Alan Coleman said:**
> 

How do I find out my Video ram?
and how would I change to 16 bit couler native resolution


regards alan C

I'm not sure about your video ram.  You could try googling the make and model number of your laptop and see if it lists it in it's specifications.  

To make xorg run in 16 bit color you need to edit your xorg.conf.  Under "Section "Screen"" change "DefaultDepth" from 24 to 16. Then a little further down in "SubSection "Display"" change "Depth" from 24 to 16.  Hit Ctrl+Alt+Backspace and you should notice a marked improvement in performance.

---

### Post by Alan Coleman on 2008-09-25
Hi thanks for getting back. Tried following your advice but the X11 file is a tricksy thing to get right for those not in the know! I post some relevant below. The persistent experience is the screen going black and other graphical probs. I can say that I have a live Knoppix CD and compiz runs as clean as a whistle from the live cd. So I know it can work!

any Ideas most welcome.

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M6 LY"
Busid "PCI:1:0:0"
Driver "radeon"
Option "AGPSize" "32"
Option "XAANoOffscreenPixmaps" "on"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "DisableGLXRootClipping" "on"
Option "AddARGBGLXVisuals" "on"
Option "AllowGLXWithComposite" "on"
Option "EnablePageFlip" "on"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon Mobility M6 LY"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection

SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
EndSection

thanks.

---

### Post by coffee_bean on 2008-11-13
My suggestion would be to view the xorg.conf file created when you use the Live CD. Can that not be done?

---

