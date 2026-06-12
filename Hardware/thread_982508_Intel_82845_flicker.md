---
title: "Intel 82845 flicker"
date: 2008-11-14
forum: Hardware
---

### Post by firecat53 on 2008-11-14
I have an older Gateway computer running Intrepid with Intel 82845 integrated graphics:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

After a while, the entire screen will occasionally flicker. It seems to happen more when watching a video in Firefox, or anytime there's a lot activity on the screen. It also seems like it gets worse after resuming from a suspend to ram. At best it's annoying, but at worst, it happens every 5 to 10 sec, and it's enough to want to reboot the computer. 

I have the stock xorg.conf file that comes with Intrepid. 
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I've tried the dpkg-reconfigure xserver-xorg, but it just gets me the same file. I've also tried changing the monitor frequency (60, 65 & 70 Hz) under the Preferences->Screen Resolution, with no effect. I had to uninstall everything to do with Compiz in order to even boot the machine.
[Xorg log here](http://pastebin.com/f14232eef)

Anyone have any ideas??

Thanks!
Scott

---

### Post by firecat53 on 2008-11-16
*Bump*
Anyone have any ideas? The flicker is almost nonexistant before a suspend. After suspend it gets so bad that web browsing and video is almost impossible.

Thanks!
Scott

---

### Post by jgreenbaum on 2009-03-21
I had the same problem running Gentoo, exact same video hardware. I found a setting in my BIOS that runs the video BIOS after resume from S3. This fixed the flicker and loss of text mode in all vts. 

Hope this helps you, it was really bugging me.

---

