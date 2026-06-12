---
title: "Display Resolution on A8V Vm SE"
date: 2010-07-01
forum: Hardware
---

### Post by soliddiesel on 2010-07-01
Hi, i used the 9.10 on my Asus A8V VM SE but the sound driver never worked, my keyboard became a turtle and display resolution was at its worst!! i installed the 10.04 its working wonders......but still have the display issues... i know few of u are using the same board, the videos and all r running smooth, but whats with the resolution, please if can one can help..!

MB Asus A8V VM SE
Display adopter AGP Bridge K8M890 AGI / PCIE

Thanks In Advance!

---

### Post by soliddiesel on 2010-07-01
Ok i went to Open Chrome support page....did this

**OpenChrome 2D driver  compilation**

 
[LIST=1]
[*]**Install needed dependencies** 

[LIST]
[*]Get  necessary tools to compile source code: sudo apt-get install build-essential
sudo apt-get install subversion
[*]
[*]
[*]
sudo apt-get install autoconf automake1.9 libtool
[*]Get all the dependency packages needed to build the driver.  In 8.04 (Hardy) and later releases run: sudo apt-get build-dep xserver-xorg-video-openchrome
[/LIST]
[/LIST]
But the last one says:

E: Unable to find a source package for xserver-xorg-video-openchrome

 Please help......Ofcourse the rest didnot work without this source package!

---

### Post by soliddiesel on 2011-07-02
1 yr and Im still stuck with the same issue!! Now im using 11.04 and the resolution has improved a bit... 1024*786 but I cant run unity, can display conky on my desktop..... its a mess!!

---

### Post by Yellow Pasque on 2011-07-02
Post your /var/log/Xorg.0.log file
openchrome is included in Ubuntu, so no need to build it yourself
> I cant run unity
That's because you don't have 3D capabilities. You can run unity-2d or xfce/Xubuntu though.

---

