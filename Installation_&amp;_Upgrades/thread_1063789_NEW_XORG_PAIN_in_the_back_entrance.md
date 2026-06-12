---
title: "NEW XORG PAIN in the back entrance"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by oucii on 2009-02-08
Have installed the U8.10 server through VMWare Workstation. Direct install into partitions, then installed Gnome and xorg, obviously when using VMWare it detects the "virtual" hardware, or exact hardware if VMWare has the option. Anyways when booting it up normally, had to do some reconfiguration... network interface, DNS in resolv.conf, etc.. and then the graphics... well after typing in "dpkg-reconfigure xserver-xorg", realized that the graphics options were all absent.. ??? 

Googled and found out that the "new" xorg does auto detection each bootup. But it doesn't here. Have an 4870 Radeon ATI, so installed the drivers for that, didn't help, gksu displayconfig-gtk, doesn't work, and tried some other things all to no avail. Same thing keeps happening, either a white screen of death, or a black screen with some weird scetchy lines on the top, after start x, or gdm.

Now I'm no advanced user, so editing the xorg.conf would be time consuming, therefore nothing can be done.. except a normal install without VMWare probably, but in this case it's necessary to do it through VMware. This procedure worked before on earlier versions of Ubuntu, so the only option is to revert. This xorg auto detect is a "shot myself in the foot" for the developers...Any suggestion?

---

### Post by Pumalite on 2009-02-08
Some people has had luck with Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

