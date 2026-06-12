---
title: "Intel Display Driver"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by benbacardi on 2007-08-09
I have a Dell Inpsirion 640M which I've dual booted with Ubuntu 7.04, and the xorg.conf file recognises the Screen Device as "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller". It has this:

```
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24

SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection

SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection

SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection

SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection

SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection

SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection

EndSubSection

```

Yet it only lists 1024x768, 800x600 and 640x480 as the possible screen resolutions. Can anyone help?  I've tried searching for topics but it's all a bit over my head, so any help is gratefully recieved.

---

### Post by Circuit99 on 2007-08-09
There are two methods of properly setting intel cards

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)


if they don't work then

Upgrade to Gusty Gibbon

Look at this post

[http://ubuntuforums.org/showthread.php?t=520662&page=4](http://ubuntuforums.org/showthread.php?t=520662&page=4)

If you need more help let me know


:popcorn:

---

