---
title: "Thinkpad X31 Ati Radeon M6"
date: 2009-11-24
forum: Hardware
---

### Post by Flix83 on 2009-11-24
Hi guys,
I just got me a used IBM Thinkpad X31 from Ebay and installed 9.10 Netbook Remix, which I didn't really liked so I moved on to Xubuntu which I really like. But there is this one Problem with the Graphic Card. Everything is fine but there seems to be a problem with the overlay or something, because the Tooltips from Pidgin and the NetworkManager are all pretty ****** up. I 've atached a screenshot of the Problem.

---

### Post by konradpiskorz on 2009-11-24
The only thing I can think of is editing your xorg.conf file with settings optimal to your video card.

Section "Device"
       Identifier      "ATI"
       Driver          "radeon"
       Option          "AccelMethod" "XAA"
       Option          "AGPMode" "4"
       Option          "AGPFastWrite" "yes"
       Option          "EnablePageFlip" "on"
       Option          "RenderAccel" "on"
       Option          "DynamicClocks" "on"
       Option          "BIOSHotkeys" "on"
EndSection

By far the most important setting here is "AccelMethod" "XAA", which dramatically improved graphics performance for Compiz and related desktop effects, while eliminating certain graphics errors. The other settings combined provided an improved glxgears performance of about 20% while not affecting Desktop performance much. 

This is taken verbatim from a now defunct site. The google cache is [http://74.125.93.132/search?q=cache:WGQHLFjdtOEJ:www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000+http://stier.is-a-geek.com/~moinmoin/MarksWiki/LinuxRadeonM6LY/Conf1&cd=1&hl=en&ct=clnk&gl=ca&client=firefox-a]("http://74.125.93.132/search?q=cache:WGQHLFjdtOEJ:www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000+http://stier.is-a-geek.com/~moinmoin/MarksWiki/LinuxRadeonM6LY/Conf1&cd=1&hl=en&ct=clnk&gl=ca&client=firefox-a")

---

### Post by mac9416 on 2009-11-24
Howdy, Flix83,

This problem has been seen on a lot of Thinkpads since the 9.10 upgrade. You can read a lot about it here: [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406)

But more likely you want to get straight to the solution provided by zanka in that thread.

Add these lines to your /etc/X11/xorg.conf (if the file does not exist, create it):

> # To avoid unreadable windows.
Section "Device"
	Identifier	"Radeon7500"
	Driver	"ati"
	BusID	"PCI:1:0:0"
	Option	"RenderAccel" "false"
EndSection

Worked like a charm for me. Good luck!

---

### Post by Flix83 on 2009-11-26
Thanks mac9416, that one worked for me too.

---

### Post by utnubuuser on 2009-11-26
Likewise --- X31 Ati M6 LY

---

### Post by Flix83 on 2009-11-27
Okay Guys, 
I'm not really sure if I should start a new Thread for this but since this is a very small problem (and I feel like a total idiot) I'll first try this thread. 
On IBM Laptops there is the tpb program which should be run on system startup and it needs root priviledges. I've tried starting it in rc.local which failed. After making /dev/nvram writeable for me and putting it into .profile it was started twice. How is this done right?

---

### Post by utnubuuser on 2010-03-12
I don't use the rendering or compiz, and I've found that using the VESA driver is considerably easier on resources than the ati driver
ie. using ati, TOP shows xorg average CPU usage of around 13%-33%,(only moving the mouse around), whereas using vesa keeps xorg's CPU usage at 1.2%-12%.

The VESA driver also solves the issue of green artifacts in GIMP

---

