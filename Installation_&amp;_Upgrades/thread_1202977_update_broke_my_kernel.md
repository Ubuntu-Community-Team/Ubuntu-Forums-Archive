---
title: "update broke my kernel"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by NicholasMolhoek on 2009-07-02
Ive been running Ubuntu 9.04 on my Asus A4K laptop for about a month now, with relatively few problems (the main one being no picture in offline video playback), i also installeed KDE the day before yesterday (to see if i could play videos in it) this wasn't a problem, downloaded and installed fine, I booted into KDE and Gnome with out anyproblems yesterday and today, but today when I was in Gnome there were several updates availiable i clicked install and it did its thing and asked for a system reboot, I closed what i was doing and clicked ok. 
Now my system will not boot at all. 
Grub comes up and i can select the different boot options;
Ubuntu 9.04, Kernel 2.6.28-11 and 2.6.28-13, with both normal and recovery mode,
there is also a memtest86 option (which seems to be working)
when i try to boot normaly the screen gos blank and the hdd light starts flashing slowly. if i try to boot into recovery mode (either kernel) I get this;

...
Begin: Mounting root file system... ...
/init: line 217: syntax error: 0xacpi=off
[    2.575828] Kernel panic - not syncing: Attempted to kill init!
[    2.575891] Dumping ftrace buffer:
[    2.575945]    (ftrace buffer empty)

and thats where it stays.
I can't seem to boot from cd either, but this is probably an issue with the hardware.
My Home directory is aa seperate partition, so if i reinstall ubuntu i'll probably still have all my files, but i'd still like to know what went wrong, or if there is a simple fix :(
thanks 
- Nick

---

