---
title: "widescreen display stuck in 1024x768"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by yippy on 2005-02-14
I have a HP zv5380 laptop, which has a 1280x800 resolution widescreen display, AMD64 and Geforce 440 Go.  I installed Warty, then added sources and dist-upgrade'd to Hoary.

First off, the text console looks great.  But in X, it just doesn't like widescreen.

For some reason, it will only use 1024x768 and show it in the upper left corner.  The bottom 32 pixels mirror the 768th line, and there's a narrow vertical strip out to the right side that mirrors a strip about an inch into the working area.  I can't get it to do anything else.  It seems to work great within that area, though.

In Gnome's resolution selector, it initially only showed 1024x768, 800x600, and 640x480.  I checked xorg.conf and only 1280x800 is defined.  I added 1024x768 to the Modes line and after that only 1024x768 appeared in the list.  I was able to add 1280x1024 also, and it would let me switch to it, but the shape of the display stayed the same.

I've tried several ModeLines parameters.  I copied some from several different people, none of them had my exact notebook, though.  I also tried generating my own using one of the web forms that do that, but that didn't work either.  No matter what I change, it always looks exactly the same.

I'm completely out of ideas.  If there's anything I haven't tried yet I'd really appreciate hearing about it.

Joejoejoe

---

### Post by Strider on 2005-02-14
Did you verify you have the right drivers for your video card?  Under the Device section in the xorg.conf, what's listed there?

---

### Post by yippy on 2005-02-15
The nv driver caused my screen to flash like the refresh rate was off, although at least it filled the whole screen. :)  I've read other people with a similar problem.  I installed nvidia-glx and that got me to where I am.  For some reason I had to manually add it to /etc/modules, though.

Even the original nvidia logo is in the weird resolution I talked about.

Joejoejoe

---

### Post by yippy on 2005-02-15
Here's what's in my xorg.conf right now:
```

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Modes"
        Identifier "16:10"
        #1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
        ModeLine "1280x800" 83.5 1280 1344 1480 1680 800 801 804 828
        # 1280x800 @ 75.00 Hz (GTF) hsync: 62.62 kHz; pclk: 107.21 MHz
        #Modeline "1280x800" 107.21 1280 1360 1496 1712 800 801 804 835
        # 1280x800 @ 85.00 Hz (GTF) hsync: 71.40 kHz; pclk: 123.38 MHz
        #Modeline "1280x800" 123.38 1280 1368 1504 1728 800 801 804 840
        # 1280x800 @ 100.00 Hz (GTF) hsync: 84.80 kHz; pclk: 147.89 MHz
        #Modeline "1280x800" 147.89 1280 1376 1512 1744 800 801 804 848
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       40-85
        VertRefresh     60-100
        Option          "DPMS"
        UseModes "16:10"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
EndSection

```

I have all the entries in Modes and the refresh rates I do because I'm not sure what my display uses, so I was experimenting with several different ones.  None of it made any difference, though.

Joejoejoe

---

### Post by jerome bettis on 2005-02-15
it looks like you and i have the same display, but with a different controller. 

this config here puts me at 1280x800

Section "Modes"
        Identifier "1280x800"
        # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
        ModeLine     "1280x800" 83.5 1280 1344 1480 1680 800 801 804 828


and it's exactly the same as yours.  except for the identifer "1280X800" instead of "16:10".  try changing that and see what happens.

---

### Post by yippy on 2005-02-15
The Identifier is just a label you can refer to in the Monitor section with UseModes.  I actually started out with "1280x800", then changed it.

I managed to get it working finally, after many hours of work.  All I did was change back to the nv driver.  Apparently there's something wrong with the latest nvidia accelerated driver.  Well that's good enough for me for now, I'll try it again when a new driver comes out.

Thanks for your help!

Joejoejoe

---

