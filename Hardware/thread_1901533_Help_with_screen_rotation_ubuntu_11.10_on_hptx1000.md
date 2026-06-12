---
title: "Help with screen rotation ubuntu 11.10 on hptx1000"
date: 2011-12-28
forum: Hardware
---

### Post by vfd000 on 2011-12-28
I have an hp tx100 whith ubuntu 11.10.  the touch screen works fairly well just some calibration issues, however I seem to be unable to get the screen to rotate. I've tried debian, fedora and a couple of other distros, however only fedora will rotate out of the box, and even so the touch screen seems to be inverted. I'm not sure if I need to enable screen rotation or what. I've tried quite a few online resources but keep coming up short. Even on occasion messing up my display completely having to use ctrl-alt-f1 to delete a xorg.conf file I created, unaware that my proprietary nvidea driver uses a xorg.conf.d file. In short i've tried everything I can think of.
 When I run $ lspci |grep VGA  it comes up with
 00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2) 
 i'm using the nvidea accelerated graphics driver (version current)[recomended]. I've tried the other proprietary drivers but they all just cause more issues.
 When I run xrandr -o right I come up with
 $ xrandr -o right 
 X Error of failed request:  BadMatch (invalid parameter attributes) 
   Major opcode of failed request:  154 (RANDR) 
   Minor opcode of failed request:  2 (RRSetScreenConfig) 
   Serial number of failed request:  14 
   Current serial number in output stream:  14 
 

 

 my xorg.conf file reads\
 $ xrandr -o right 
 X Error of failed request:  BadMatch (invalid parameter attributes) 
   Major opcode of failed request:  154 (RANDR) 
   Minor opcode of failed request:  2 (RRSetScreenConfig) 
   Serial number of failed request:  14 
   Current serial number in output stream:  14 
 

 any help would be greatly appreciated.
 -Axl

---

