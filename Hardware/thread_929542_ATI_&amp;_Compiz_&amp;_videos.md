---
title: "ATI &amp; Compiz &amp; videos"
date: 2008-09-25
forum: Hardware
---

### Post by valmo on 2008-09-25
Hi all!!! i'm new to the forum and to ubuntu (but is not a problem , i war a DOS user many years ago)!!!
i installed few days ago Ubuntu 8.0.4 and all works good!
But still a little problem...ATI uses proprietery drivers (for mine the open ones doesn't works ATI X1650pro PCI-e) and i think that compiz don't like it so much!
The problem is that when i activate the 3d effect on desktop, when a i look movies (specially Dvix/Xvid) in fullscreen mode, movies seems loose quality and fps. With all king of programs (mplayer, VLC, totem, totem-xine). In default size windows all work good!
If i disable compiz and 3d effect, movies run right also in full screen.
Ah...my video oputput (x11) is Vx.
In many forums and blog i find only that ATI x series (from x1100) have this problem, but i notice something strange...
someone told me that if i zoom desktop on the movie windows (with "start"key+mouse wheel) movies is displayed well. i tried this and IT WORKS!!! but...the mouse pointer in the middle of the desk....:mad:
There's something i can try to make all work good? Does an apps that told system to manage fullscreen windows like "zoom desktop"?
Please help!!! if i can adjust this problem i can move windows in the trashcan!!!:)

---

### Post by WWSmith36 on 2008-09-25
Can you show me the output of fglrxinfo.

---

### Post by valmo on 2008-09-25
yes...sorry for the late..

fglrxinfo
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7412 Release


i've alredy try to update the drivers both manual (from ATI website) and envy, but system goes worth, it can't find monitor settings and graphic card. The only way i've found to enable 3d accelleration is install from system->administration->hardware driver and check the option "use proprietary drivers"

thank you for your help!!

---

