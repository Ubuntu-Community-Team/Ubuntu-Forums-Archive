---
title: "Kubuntu Linux display problem on Acer laptop"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by Charles Ng Cho Hui on 2005-11-24
Hi,

I face a problem where i successfully installed the Kubuntu Linux 5.1 (Breezy Badger) into my Acer Travelmate 4102 WLMI laptop, but no display after load all the stuff...

i tried to reconfigure - xserver-xorg

[sudo dpkg-reconfigure xserver-xorg]
and select VGA, instead of ATI driver...then choose resolution 400x300 (lowest resolution) and color depth 8.

I can login to kubunto, but it load the low resolution...and terible display..

I also tried to download the graphics driver from ATI,
ati-driver-installer-8.19.10-i386.run
but the checksum incompatible.

FYI, my LCD display is 15.4" WXGA wide tft LCD, while my Graphic is ATI Mobility Radeon X700 PCIe with 64MB VRAM.

Anyone know how to solve this problem?

THANKS a million!  :)

---

### Post by fogNL on 2005-11-24
I have the same issue with my Aspire 1694.  To fix it, open up your /etc/X11/xorg.conf in console, in your "Device" section add the following:

Option     "MonitorLayout"    "LVDS,TMDS"



Here is my Device section:

> 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MonitorLayout"         "LVDS,TMDS"
EndSection


Save your file and restart your X server, and all should be well :)

---

