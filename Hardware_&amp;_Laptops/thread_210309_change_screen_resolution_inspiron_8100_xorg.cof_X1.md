---
title: "change screen resolution inspiron 8100 xorg.cof X11"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by Pugi! on 2006-07-06
I have installed dapper drake on my dell laptop inspiron 8100. Normally I work with the default resolution 1400x1050. As I recall this was default resolution after installing Breezy Badger. After installing dapper drake, default resolution is 1O24x768 with a refresh rate of 0 Hz. And the only choices I have are 640x480, 800x600 and 1024x768. I already googled but apperently the xorg.conf has a different layout in dapper drake. Si I don't know where to start now.
What steps should I take to get this fixed ?

Below you'll find part of my xorg.conf

...
Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 Go]"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 Go]"
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


thanx,

Pugi!

---

### Post by Dr. Nick on 2006-07-06
If you want the 1400x1050 res then just add it to all the depths and save then log out/on and see if you can change it. Add it just like I have below in red to each depth and see if that works

                Depth           24
                Modes           "                 Depth           24
                Modes           [COLOR=Red]"1400x1050" [/COLOR]"1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by Hellkeepa on 2006-07-06
HELLo!

It's also very likely that you have to use "i925resolution" to manually add the wide-screen format to the BIOS, and you'll find lots of information about this by searching on the forum. ;)

Happy codin'!

---

### Post by Pugi! on 2006-07-07
I tried the solution from ubuntuguide.org first, but after installing nvidia I ended up with an ATI reference in my xorg.conf. Nothing to see anymore ... duh.
Then I found this link:
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)
with a link to :
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I follewed method 1. Rebooted. And what do you know : resolution 1400x1050 and 60Hz refreshrate right from the start.

Pugi!

---

