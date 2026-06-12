---
title: "How do you list the possible graphic card resolutions?"
date: 2010-09-18
forum: Hardware
---

### Post by dargaud on 2010-09-18
Hello all,
I just spent 10 minutes googling for a way to list all the resolutions available on my graphic card. I do not want to know the resolutions supported by my current monitor, which are available in [System settings][Size & Orientation][Size]. It also seems different from what you get by doing "*sudo hwinfo --framebuffer*" where the highest resolutions are missing. Also spec sheets of graphics cards rarely specify the resolutions.

I want this in order to plan a high-res monitor change.

---

### Post by Yellow Pasque on 2010-09-18
Depends on driver, but if you're using open-source drivers:
```
xrandr -q
```

---

### Post by dargaud on 2010-09-19
I don't think xrandr is correct as the 1920x1200 resolution is missing (or maybe it's assumed under the 'max 1920x1920' ?). And I know this one works from my past (now dead) monitor. Let's see:
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      60.0*+   50.0  
   1776x1000      60.0 +   50.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0     50.0  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0     50.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     72.8     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
```
```
$ sudo hwinfo --framebuffer
[sudo] password for dargaud: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.wiTiGIoBPmB
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RS780D"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RS780D"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```
In Windows it's possible to get the graphic card resolution by doing [View all modes] in the advanced display tab, but I can't try that.

---

### Post by cascade9 on 2010-09-20
> **dargaud said:**
> I don't think xrandr is correct as the 1920x1200 resolution is missing (or maybe it's assumed under the 'max 1920x1920' ?). And I know this one works from my past (now dead) monitor. 


"maximum 1920 x 1920" is totally wrong. I dont know of any monitor that ran at that resolution, and even if it did, its missing 1920x1200 and 1920x1440. 

What card is it? If its an ATI or Intel, finding the info can be harder than nVidia, but with nVidia, its pretty easy.

---

### Post by dargaud on 2010-09-20
It's an mobo-embedded ATI Radeon HD 3300. But the question wasn't specific to that card, but to any card.

---

### Post by Yellow Pasque on 2010-09-20
> **cascade9 said:**
> "maximum 1920 x 1920" is totally wrong.
Pedantic side-note: The maximum reported by xrandr is the largest size of the virtual screen, which can be greater than what you monitor can display. If so, you move around (i.e. scroll) it by moving your mouse to the edge of the screen. This happens inadvertently to some systems when X autodetect screws up and then users make threads like, "Oh no! I can't see all of my desktop!"

Anyway, I should have read the OP more closely.
The RadeonHD 3300/785G can drive a 1920x1200 display with no issue. You won't even need a dual-link DVI cable (though most are nowadays).

---

### Post by efflandt on 2010-09-21
There is no ready made list.  For default drivers /var/log/Xorg.0.log may tell you what resolutions X has found from the EDID of the display, but sometimes it rules out resolutions that the video card and display are actually capable of, and you can add resolutions that do not exist using **xrandr**.  And then it depends if you found a proper modeline from **cvt** or **gtf** commands or some other source.

In some cases maximum reported by xrandr is maximum that video card and its memory are capable of, but in other cases maximum is just the maximum of already listed resolutions or current display.  For example one laptop lists maximum 4096 x 4096, so I can easily add a 1920x1080 mode for 1080p HDTV VGA.  But a low end laptop lists maximum 1360 x 1360, and the highest resolution I can set for the 1080p HDTV is 1360x768 (which works full screen, but is not optimum).

I think my desktop only reported maximum 1920 x 1080 when it had default drivers because that was the native resolution of the DVI to HDMI connected HDTV, but the GT220 video card with 1 GB on-board RAM and several GB of shared RAM is certainly capable of more than that if I had a higher resolution monitor.

xrandr does not really report properly for nvidia driver because it says my display is 50 Hz when NVIDIA X Server Settings correctly show it as 60 Hz

```
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0     52.0     53.0     54.0     55.0
...
```

---

### Post by cascade9 on 2010-09-21
> **dargaud said:**
> It's an mobo-embedded ATI Radeon HD 3300. But the question wasn't specific to that card, but to any card.

As far as I know, the maximum resulution should be 2048x1536 (VGA) and 2560x1600 (DVI). I think HDMI has a max res of 1980x1080, but I didnt get that from ATI, so I cant know for sure.

> **Temüjin said:**
> Pedantic side-note: The maximum reported by xrandr is the largest size of the virtual screen, which can be greater than what you monitor can display. If so, you move around (i.e. scroll) it by moving your mouse to the edge of the screen. This happens inadvertently to some systems when X autodetect screws up and then users make threads like, "Oh no! I can't see all of my desktop!"

Heh, I didnt know that. Thanks for the info ;)

---

### Post by dargaud on 2010-09-21
I'm really surprised at the variety of all the answers. Shouldn't it have all been solved by now by some standard query to the card via a common API or something ?

---

