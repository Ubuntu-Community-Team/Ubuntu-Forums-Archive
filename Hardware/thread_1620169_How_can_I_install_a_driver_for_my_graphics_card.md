---
title: "How can I install a driver for my graphics card?"
date: 2010-11-12
forum: Hardware
---

### Post by macnomore on 2010-11-12
I have a
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```graphics card
First of all, is that graphics card automatically supported by Ubuntu 10.10?
I know that I can install a driver for it with System->Administration->Additional Drivers, but it says that "No proprietary drivers are in use on this system.", and shows no drivers installed. Where does the Additional Drivers application search for proprietary drivers? How can I find and install the driver I need for my graphics card?

One more problem:The attachment (the .png screenshot of the monitors preferences) does not look right to me. Believe it or not, those are the only options. How can I get my computer to detect my monitor?

---

### Post by KL_72_TR on 2010-11-12
Hello. I have a NVIDIA Geforce GTS 250. For my monitor I did this: System > Preferences > Monitors and came a warning  [IMG]http://ubuntuforums.org/album.php?albumid=2101&pictureid=6997[/IMG] here I clicked 'Yes'[IMG]http://ubuntuforums.org/album.php?albumid=2101&pictureid=6999[/IMG].
To find the proprietary is easy: System > Administration > Hardware Drivers => [IMG]http://ubuntuforums.org/album.php?albumid=2102&pictureid=7000[/IMG]. I'm not quite sure but I think you have 'Integrated Graphic Card' and I don't know how to deal with this. Also 'Device Manager' is a helpful tool: Applications > System Tools > Device Manager => [IMG]http://ubuntuforums.org/album.php?albumid=2103&pictureid=7001[/IMG] Here click 'View' and check 'Device Properties'[IMG]http://ubuntuforums.org/album.php?albumid=2103&pictureid=7002[/IMG][IMG]http://ubuntuforums.org/album.php?albumid=2103&pictureid=7002[/IMG].
I hope you found a better solution.

---

### Post by 73ckn797 on 2010-11-12
My Toshiba Laptop lists no drivers but I can set the "Visual Effects" to maximum. See attached image. The laptop has the Intel graphics chip.

The resolution was automatically set to max. Anything else did not look as good.

---

### Post by cascade9 on 2010-11-13
> **macnomore said:**
> I have a
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```graphics card
First of all, is that graphics card automatically supported by Ubuntu 10.10?
I know that I can install a driver for it with System->Administration->Additional Drivers, but it says that "No proprietary drivers are in use on this system.", and shows no drivers installed. Where does the Additional Drivers application search for proprietary drivers? How can I find and install the driver I need for my graphics card?

Yes, that card is automatically used, and no, there aren't any proprietary drivers for it. All the intel video drivers are open source (AFAIK anyway). 

As for the monitor, theres a probelm with EDID. 

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

---

### Post by macnomore on 2010-11-15
> **cascade9 said:**
> Yes, that card is automatically used, and no, there aren't any proprietary drivers for it. All the intel video drivers are open source (AFAIK anyway). 

As for the monitor, theres a probelm with EDID. 

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)
Okay, more questions:
1.How can I fix my EDID problem? Should I get a new monitor?
2. How outdated is my video card, and should I replace it with a newer one? Anything majorly OpenGL is slower than it should be(about .5 fps to my estimate when I try Nexuiz, but then again, that might have something to do with the EDID problem for all I know), and the desktop effects won't work.

---

### Post by cascade9 on 2010-11-17
1- I'm not sure how you fix the EDID problem, I've never had it so I've never had to figure it out. 

2- Very, very outdated. Intel 845 video was outdated on release (2002) as it was using an intergrated i740 video chip (released in 1998 and outclassed by the nVidia/ATI/3DFX etc cards avaible then). 

You might be able to find a cheap AGP or PCI video card that would work, but I wouldnt spend to much on any upgrade for a system that old.....

---

