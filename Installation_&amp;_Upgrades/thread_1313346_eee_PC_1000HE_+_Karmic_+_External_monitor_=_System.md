---
title: "eee PC 1000HE + Karmic + External monitor = System freeze"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by jimtshea on 2009-11-03
Installed 9.10 with no problems on my 1000HE (I don't use the Fn or Silver buttons so I don't care if they work or not). The OS works fine, installed my apps and restored my data from backup and life is good. That is until I try to connect to an external monitor or projector. Then the system locks up.

When running 9.04 I had to edit the xorg.conf file to set the Virtual Resolution higher. With 9.10 there isn't an xorg.conf file any more. I created one containing my 9.04 settings as I had read that a xorg.conf will be used if it exists. Alas no satisfaction, it still locks up.

xrandr reports:
  Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
  VGA1 disconnected (normal left inverted right x axis y axis)
  LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
     1024x600       60.0*+
     640x480        59.9 

I'm not sure what incantation to use at the command line to increase the Virtual Resolution (if that's even the problem). I tried the following with the following results:
$ xrandr --output VGA1 --mode 1920x1200
xrandr: cannot find mode 1920x1200

Anybody have ideas or links that describe how to get high resolution connection to an external monitor without locking up?


Thanks

Jim

---

### Post by eats7 on 2009-11-03
i am having the same problem. same resolution same os and same computer. 
can anyone help? 
i havent had ubuntu installed on this machine before so i dont have another xorg.conf. and this 9.10 doesnt have one.

---

### Post by mephx on 2009-11-04
Hello,

I'm having the same exact problem. Asus 1000he Ubuntu Karmic 9.10

Found a workaround and possibly a lead to the bug fix.

1 - Open Display Properties
2 - Turn Off Mirror Screens
3 - Turn Off Internal Screen
4 - Turn On External Display
5 - Select desired resolution for External Display
6 - Apply Changes

This only gets the external Display to work, I haven't found a way on getting both to work at the same time.

Will now fill a bug report if one does not exist.

Cheers,
mephx

---

### Post by eats7 on 2009-11-04
yes ive gotten the second one to work no problem too, but what i wanna get working is the extended desktop. have the external my primary, and the netbooks screen secondary.

---

### Post by mephx on 2009-11-05
Hey,

Desktop effects (compiz) seems to be the cause of this. Turn it off and use metacity in the meanwhile. I'm now with 2 screens setup on my 1000he.

Here's the lauchpad url for the bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438000/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438000/)

Cheers,
Sérgio

---

