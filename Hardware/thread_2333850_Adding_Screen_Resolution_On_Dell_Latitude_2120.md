---
title: "Adding Screen Resolution On Dell Latitude 2120?"
date: 2016-08-13
forum: Hardware
---

### Post by 1unknowngal1 on 2016-08-13
Hello, I recently purchased a used Dell Latitude 2120 which had Windows 7 on it. I decided to add Linux to it instead, trying various flavors, such as Ubuntu MATE, Linux Mint MATE, Xubuntu, Lubuntu, Trisquel, and even Puppy Tahr Linux, and I couldn't get any of them to show a resolution above 1024 x 768. I looked around online to see if I could add another resolution to the settings, following instructions mentioning xrandr, but nothing I did changed anything about the resolution. Has anyone successfully been able to run any flavour of Ubuntu or Linux on the Dell Latitude 2120 with the correct resolution (which I read online was 1366 x 768)? (I also had another issue where the Wi-Fi would not work when trying to install distros, I would have to hook the Latitude up directly to my modem/router, but that's for another thread.) I would very much like to get this little machine running if possible. Thank you for any help sent my way!

---

### Post by mörgæs on 2016-08-14
Hi, welcome to the fora.
Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Yellow Pasque on 2016-08-15
A quick google shows this netbook came with a few variants of Atom N4xx/N5xx CPU's. In other words, GMA3150 graphics. This GPU should work out of the box on modern Linux distros.

In addition to lshw output, I'd suggest posting or pastebin of /var/log/Xorg.0.log (use code tags).  1024x768 could indicate that generic vesa driver is being used for some reason.

---

### Post by richarduie2 on 2016-12-20
Open a terminal and run xrandr without options to get your system info. On my 2120 (1.66 GHz processor, 2 GB RAM, Mint 17.3, KDE 4.13.2), I get the following:

~~~~~~~~~~~~~~~~~~~~
[FONT=courier new]richard@tanuki:~ > xrandr
Screen 0: minimum 8 x 8, current 1536 x 900, maximum 32767 x 32767
LVDS1 connected primary 1536x900+0+0 (normal left inverted right x axis y axis) 223mm x 125mm panning 1536x900+0+0
   1024x600       60.3*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT]
~~~~~~~~~~~~~~~~~~~~

Note that the 2120's primary display is cited as "LVDS1" - that's how you reference it using the xrandr --ouput option. I use a display resolution of 1536x900 (that's reported in the output above). In order to get that resolution, I run the following bash script, scaleDisplay.sh, at start-up:

~~~~~~~~~~~~~~~~~~~~
[FONT=courier new]#!/bin/bash
xrandr --output LVDS1 --mode 1024x600 --panning 1536x900 --scale 1.5x1.5[/FONT]
~~~~~~~~~~~~~~~~~~~~

I've also tried:

[FONT=courier new]xrandr --output LVDS1 --mode 1024x600 --panning 1280x768 --scale 1.25x1.28[/FONT]

However, I much prefer the 1536x900.

I've used the same xrandr tweaks on an ASUS netbook (same processor/memory combo) that I've owned for a few years; different display name but same results under Kubuntu and Kali.

P.S. KDE/Plasma is unworkably resource-intensive under Mint 18 and Kali rolling...had to revert to 17.3 for both the ASUS and the Dell.

---

