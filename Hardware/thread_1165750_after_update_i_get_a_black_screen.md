---
title: "after update i get a black screen"
date: 2009-05-20
forum: Hardware
---

### Post by nemesisinfinity on 2009-05-20
I have installed 9.04 3 times now and everytime after i do the update manager and its done i'm fine till i reboot then i get the ubuntu loading screen then my monitors give me a rainbow colored ubuntu logo across the top and then they go into standy....it still logs in cause i hear the music play...i can list all the updates that are available if you want i just dont want to go through them all one by one reinstalling every time...here is some info on my system

ubuntu 9.04 64bit
m2r32-mvp mobo
amd 4800+ 64 bit cpu
4 gigs of ram
radeo 4850 gpu 
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV770 [Radeon HD 4850] [1002:9442]
(found that cmd line on another post to show you info)
 anything else you need let me know

another note i installed WoW and when i try to run it with wine takes a bit to load and the screen is garbled

---

### Post by LinuxDanP on 2009-05-21
This is probably bad advice, but it might have something to do with your graphics drivers. I just did a clean 9.04 install, and every time I try to install the nVidia driver for my graphics board, it will not boot into any graphical environment. I can do a terminal login, and switch between tty's, but nothing else. Did your update include a graphics board driver? If so, which driver? I'm just curious, I saw that one other user had an identical problem to mine, which is described here: [http://ubuntuforums.org/showthread.php?t=1162689](http://ubuntuforums.org/showthread.php?t=1162689).

---

### Post by nemesisinfinity on 2009-05-21
bad thing is that i looked at the list of updates and none of them seem to say anything about graphics....one of them is for power management could that be it?

---

### Post by LinuxDanP on 2009-05-21
Well, I really don't know, it probably isn't graphics related since it didn't update graphics drivers. Do you just use the drivers that Ubuntu has by default, or do you use a proprietary driver from your board's manufacturer? It seems most likely that your problems are related to graphics drivers, maybe one of the packages that was updated has a driver conflict. Of course, I could be all wet on that, I'm probably giving you bad advice. It could very well be gdm, was it updated? I assume that you are using gnome, my problem seems to be a conflict between kdm and the nVidia driver, although your problem seems to be completely different.

---

### Post by nemesisinfinity on 2009-05-21
gdm i think i remember seeing that ill have to reboot out of vista to ubuntu to check....I may just go through and just do 1 update at a time till it crashes and post that....but man i hate reinstalling it every time


okay i did some of the updates and im still working so good
I have 5 that i haven't done they are

acpid
compiz config-backend-gconf
gnome-settings-daemon
libgl1-mesa-dri
libgl1-mesa-glx

think it could be any of those?  I'm goin to look up the libgl1-mesa updates now to see what they do



ok well i installed the ati proprietary driver by going to hardware drivers in admin and was gettin the same thing.....had to do abunch of stuff i barely understood to get back and running
apt-get remove --purge xorg-driver-fglrx 
and it started in low res mode and a bunch of stuff but now im back


i think its got to do with my graphics driver so gotta figure out how to install it i guess

---

### Post by nemesisinfinity on 2009-05-22
going to try and do a manual install of the driver for ati's 4850

---

