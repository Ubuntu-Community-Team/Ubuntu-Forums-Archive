---
title: "Svideo to lcd tv"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by berlinbrown on 2008-02-02
I am trying to setup svideo output from a media type PC to a lcd tv.  So far, it shows up but the output is kind of wavy and gets worse over time, so I hope I am not messing up the TV.  What should I do to get rid of this.  Also, what kind of screen resolution do you think I should use.

Tv: insignia 26inch lcd hdtv (also has svideo, hdmi, vga)

I have a vga, but I am setting that up for the CRT monitor.  I might be able to use the HDMI output?

The only thing I might see relevant is the Monitor/Device in the xorg.conf.

Section "Monitor"
        Identifier      "Monitor[1] TV" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1] TV"
        Screen 1
        Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc
        Option          "TVStandard" "NTSC" #or PAL-G NTSC etc
        Option          "ConnectedMonitor" "Monitor[1]"
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection


Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Screen 0
EndSection

---

### Post by oldsoundguy on 2008-02-02
going through this myself.  svideo is fine if you are driving a crt or a standard aspect ration toob that HAS standard svideo inputs.  But it will NOT work on wide aspect HDTV units and give you wide screen  (I have a 42"). 
VGA MAY work in your case since you have a VGA input. But then again, it may not.
You need to get into the card utility to set up the second monitor.  And you want to set it up as dual view so you may adjust the resolution for the toob.
In my case, I did NOT so had to get a dual DVI-I ouput card from nVidia.  NOT HOOKED UP YET as the card is on the way.  THINK that may solve my problem

---

### Post by berlinbrown on 2008-02-02
I don't have the vga availble, I am using that for the monitor.  I do have a hdmi slot available and I thought about hdmi-vga-converter because I dont have a hdmi cable and those are expensive.  E.g. I have 3 outputs from the graphics cards.  vga (going to computer monitor), svideo (currently to the lcd tv), hdmi (currently empty).

How would I convert where it says svideo, convert it to hdmi?  Is it really VGA?

But thanks for the insight.

---

### Post by oldsoundguy on 2008-02-02
I have a couple of nVida 6200 cards .. they come with the svideo, vga and DVI-I connector (not HDMI). 

[http://www.datapro.net/techinfo/dvi_info.html](http://www.datapro.net/techinfo/dvi_info.html)

 IF you are running an lcd monitor, you should be using the DVI-I connector as you will get a LOT better picture. that will free up the VGA.  Then you can have VGA to VGA .. but sure not certain you will be able to get wide aspect ratio because of your PRIMARY display .. if it is not wide screen, may be difficult to make the toob display wide screen because of the SOURCE.  NOT SURE ABOUT THAT AT ALL!

---

