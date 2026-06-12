---
title: "command equivalent of a USB unplug/plug in"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by jonas73 on 2007-10-31
i have gutsy installed on a zonbu ([www.zonbu.com](www.zonbu.com)) and i'm having trouble with two USB connected drives. both are plugged in at boot time and automounted with fstab (using labels). everything used to work just fine, but as of the other day one of the drives refuses to be seen/mounted. i swear i didn’t change anything except accepting the daily updates. i don’t remember seeing anything kernel related though? if i unplug the USB cable and plug it back in and run "sudo mount -a" it works fine. i did however notice that it connects as /dev/sdc while before when everything was working it used to be /dev/sdb. if i do not unplug/plug back in the USB cable nothing is seen (by for example gparted) on /dev/sdb or /dev/sdc only the first drive (that works fine) on /dev/sda is seen. if i switch USB ports between the two drives the working/not working order also switches. so it's not the drive but rather the USB port that i'm having problems with. i’ve read a bunch of posts regarding problems with USB ports and gutsy so i'm hoping this is a kernel?? issue that will be resolved, however in the meantime i'd like to add a unplug/replug command @ boot time so that i can run "sudo mount -a" and have everything work without physically having to unplug/replug the cable. is there such a command? i.e. a command that is equivalent to unplug/plug back in a USB cable? also, if anyone has any ideas of things i could try to get things really working (as supposed to this ugly fix) i'd gladly try anything. so far i've tried every boot option (irqpoll etc) i could find. sorry for the long post. thanks!

---

