---
title: "Problem with Intel 915GM in ubuntu 5.10"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by thevenin on 2006-03-05
my laptop: HP nx6120 with 915 GM (Intel integrated display chipest)
my system: ubuntu 5.10 breezy badger

problem:

now, my laptop display things in "vesa" mode. Namely, in this file,
"/etc/X11/xorg.conf",
"dirver" of "device" is "vesa".
the performance of "vesa" is so ugly that i can't bear any more:(

How can I install Intel 915GM in ubuntu 5.10 and make the driver work?
thanks!!

---

### Post by thevenin on 2006-03-05
PS:
In FC4, I could install the driver with .rpm downloaded from Intel's website. And FC4 provides a graphic way to select display card and screen. After proper setting, 915GM works.

Now in ubuntu, I "alien" the .rpm driver to a "deb" file, then install it. but nothing    changed.

what shall i do.............?
thanks.

---

### Post by kairu0 on 2006-03-05
For me, it was just a matter of configuring the right modelines and resolution in my xorg.conf. I didn't have to install any special driver. My current driver is part of the Breezy distribution.

---

### Post by audax321 on 2006-03-05
Try changing "vesa" to "i810" that is the driver for that card. It should come with Ubuntu.. it was automatically selected for me on my laptop.

---

### Post by thevenin on 2006-03-05
[QUOTE=kairu0]For me, it was just a matter of configuring the right modelines and resolution in my xorg.conf. I didn't have to install any special driver. My current driver is part of the Breezy distribution.[/QUOTE]

could u paste the three sections of your xorg.conf here -- "device","monitor","screen" ?

I use "xresprobe i810" to identify sth, but get nothing ...

So may i have a look of yours?

thanks!

---

### Post by thevenin on 2006-03-05
[QUOTE=audax321]Try changing "vesa" to "i810" that is the driver for that card. It should come with Ubuntu.. it was automatically selected for me on my laptop.[/QUOTE]

I tried that, but the x window will break down. and the line under "driver=i810" is "pci x : x : x"(x is kind of number) that i don't know how to configure.

so could you paste the "device" section of your xorg.conf here?
thanks!!

---

### Post by audax321 on 2006-03-05
This is my Device section:

```

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```

However, my laptop is the HP DV1000, so it may be different for yours. You shouldn't have to change anything for the BusID or Identifier.

This is the Monitor section:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

```


This is the Screen section:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768"
        EndSubSection
EndSection

```

In the Screen section you should be able to replace 1280x768 with whatever resolution your screen uses.

---

### Post by thevenin on 2006-03-06
Thank you, audax321 !
With your xorg.conf, the chipest seems to take effect.
Although the performance is not so good as I expected, I will work on it for a while by myself.
 
Thank you very much.

---

### Post by audax321 on 2006-03-06
You could also try adding these lines to the device section. They won't improve the glxgears fps (which isn't a very good benchmark anyway), but I felt it made the performance a little better. Also, I hear xorg 7.0 works much better with this card. But we'll have to wait and see about that when Dapper is final. Here are the lines:

```

        VideoRam        131072
        Option          "RenderAccel"           "true"
        Option          "DRI"                   "true"

```

The VideoRam line is just there to make sure the video card uses the amount of RAM it is allowed to (128 mb). I'm not sure the RenderAccel and DRI lines do anything (they might in xorg 7.0) but I haven't noticed anything bad with them being there so I just kept them. As I said, performance "feels" better with these lines, I'm not sure if it is actually better though.

---

