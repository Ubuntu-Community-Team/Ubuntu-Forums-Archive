---
title: "Lenovo N200 B5G + S-Video"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by sagivegh on 2007-12-19
Hi,

I have Lenovo N200 B5G - Core 2 Due 1.5Mhz + Intel X3100 - 965 GMA
and I want to know,
How can I watch video via s-video on the TV.
I got Ubuntu 7.10

Thanks,
Sagi

---

### Post by sagivegh on 2008-01-17
Somebody, pls....:(

---

### Post by rowtc2 on 2008-01-17
You have an video output from your soundcard ? Connect the laptop to lcd/tv and set the videographic card .

---

### Post by sagivegh on 2008-01-17
Again, I have intel 965gm and I want to know how to use the TV-OUT

---

### Post by pcgomes on 2008-05-07
I made S-Video work with my Intel 965 GM board following the information at this site:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Notice that you should add the line below to you "Device" section.

Option          "monitor-TV"   "TV"

Also, you should create a new "Monitor" section, to refer to the TV. The lines below might be just fine:

Section "Monitor" 
       Identifier      "TV" 
       Option          "Ignore" "False" 
EndSection 


Last, there is the MAGIC trick. Although you configure everything just fine and xrandr tell you TV is connected, you may not see anything at you TV. Try to reboot your computer with the s-video cable plugged and the TV on. That's the only way I can make to work.

---

