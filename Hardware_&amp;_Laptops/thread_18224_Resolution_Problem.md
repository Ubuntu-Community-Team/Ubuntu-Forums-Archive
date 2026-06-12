---
title: "Resolution Problem"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by Shinkan on 2005-03-05
Hi !

I've juste set up Ubuntu Hoary (Hoary 5.04 array 6) on my laptop and I was quite happy because the previous Ubuntu didn't work.
But I can't use the 1024x768 resolution that I need (or the displayed things don't use fullscreen).
This is the lonely res i can use but Gnome & Ubuntu doesn't permit it.
I've checked xorg.conf and "1024x768" is present at each depth ...

Don't know what to do ...

---

### Post by alastair on 2005-03-05
Look in the X server log :

/var/log/Xorg.0.log

Check for errors - perhaps show us the file.

---

### Post by Shinkan on 2005-03-05
There's no errors !

Laptop works "perfectly" but with a "800x600" resolution, and I need "1024x768" for my display to works "fullscreen" ; but gnome screen resolution utility dosen't show me more than "800x600", and I know that my laptop can (and NEED) ...

---

### Post by alastair on 2005-03-05
So, maybe Xorg is probing the monitor wrong.

Look in /var/log/Xorg.0.log

There are lines regarding the monitor probing and resolutions - look for a reason why your 1024x768 res. is not used.

---

### Post by Shinkan on 2005-03-05
I've found but I don't really understand :

(II) I810(0): Écran générique: Using default hsync range of 28.00-33.00 kHz
(II) I810(0): Écran générique: Using default vrefresh range of 43.00-72.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (800 -> 1024).
(--) I810(0): Virtual size is 800x600 (pitch 1024)
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2


Heres is my xorg.conf :

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Écran générique"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Écran générique"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection

---

### Post by alastair on 2005-03-05
You have not shown all the xorg.conf file and I might be wrong.

If I am post ALL the Xorg.0.log and all the xorg.conf.

You have ONE subsection "Display" :

SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection

Is this ALL?

If so ...

Make a BACKUP copy of the file :

/etc/X11/xorg.conf

Then edit it :

sudo gedit /etc/X11/xorg.conf

In the section "Screen" - add EXTRA subsections (you already have 1 section) i.e.

SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection

SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection

SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection

SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection

SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection


Save the file and restart X (log out / log in).

Maybe that will help.

---

