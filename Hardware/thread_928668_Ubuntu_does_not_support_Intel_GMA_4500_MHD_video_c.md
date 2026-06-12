---
title: "Ubuntu does not support Intel GMA 4500 MHD video card"
date: 2008-09-24
forum: Hardware
---

### Post by JC SHOT U on 2008-09-24
Dell Latitude E5500
Intel GMA 4500 MHD integrated video

The video card does not have drivers for Ubuntu. This video card is in a lot of the new laptops. The only way I can have video is in Low Graphics Mode. This is at 1024x768 resolution. This resolution is giving me a headache because it is stretched out. The CORRECT resolution should be at 1280x800. This is a bug that ubuntu needs to fix. 

I even reconfugured xorg.conf to manually use 1280x800. The screen had a green stripe at the top and 3 seconds later, it changed to the default 1024x768. 

Does anyone have a fix for the Intel GMA 4500 MHD?? Thanks!

---

### Post by TheCan on 2008-09-24
Hi,

please take a look in the Lenovo X200 owner's thread:

[http://ubuntuforums.org/showthread.php?t=907936](http://ubuntuforums.org/showthread.php?t=907936)

The Lenovo X200 also comes with the X4500 MHD graphics for which an inofficial driver package exists which makes it work in 8.04. I think in 8.10 it will be supported out of the box, though I don't recommend trying out the latest alpha6 due to a current issue with the Gigabit-LAN driver which can permanently damage your hardware.

---

### Post by JC SHOT U on 2008-09-24
It gives me an error. 

[B][COLOR="Red"]Error: Conflicts with the installed
package 'xserver-xorg-video-i810'[/COLOR][/B]

BUT... I did a: ```
sudo apt-get remove xserver-xorg-video-i810

```

THEN i installed the new driver thing:
[http://ppa.launchpad.net/melchiorre/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0~melchiorre-5_i386.deb](http://ppa.launchpad.net/melchiorre/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0~melchiorre-5_i386.deb)


I rebooted. but I still have 1024x768 resolution. How can I get 1280x800?

---

### Post by rasmus91 on 2008-10-31
I have Intrepid. I get 1440x900.

But when doing glxgears i only get like 300+ fps

---

### Post by PaintSplat on 2008-11-27
i have a T400 with a max resolution of 1280X800..
had to modify the xorg.conf file

[http://ubuntuforums.org/showthread.php?t=209474](http://ubuntuforums.org/showthread.php?t=209474)

Hope this helps

---

### Post by Demophobie on 2008-11-30
Hi !

Is there already a solution to this problem? 1000 fps would be nice.

Patrick

---

### Post by gtg694t on 2008-12-29
Solution can be found here: 

[http://ohioloco.ubuntuforums.org/showthread.php?p=6450032](http://ohioloco.ubuntuforums.org/showthread.php?p=6450032)
[http://ohioloco.ubuntuforums.org/showthread.php?p=6450032]("http://ohioloco.ubuntuforums.org/showthread.php?p=6450032")

---

