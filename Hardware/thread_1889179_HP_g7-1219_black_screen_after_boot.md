---
title: "HP g7-1219 black screen after boot"
date: 2011-11-30
forum: Hardware
---

### Post by Tanist on 2011-11-30
I am completely new at this and have looked around for a few days to try and figure out what I need to do to solve my problem but am unsure what steps to take.

When I try to boot into Ubuntu from a thumb drive I get a black screen after boot.  Initially I get the option to boot from the thumb drive (along with windows etc).  After choosing this option I get several seconds of text that runs up the screen and despite using f keys etc will not stop. Then I get a few seconds of black screen followed by a short musical tone.  (This also suggests that my sound card works fine.)  Unfortunately the screen remains black after that point and nothing seems to change the condition including attempting a few of the suggestions here [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535).

I am attempting to boot Ubuntu 11.10 from a thumb drive onto a new HP g7-1219wm laptop.  

Some basic specs of the machine.

AMD E-450 Dual Core (1.65GHz Vision E2)
AMD Radeon HD 6320 Discrete-Class Graphics (integral with the processor)
3 USB ports
1 VGA
1 HDMI

I found here [http://ubuntuforums.org/showthread.php?p=11502061](http://ubuntuforums.org/showthread.php?p=11502061) a thread that will eventually help me solve a future problem, once I can see the screen.  (This also gives me hope that the problem can be solved.)

I would like to be able to keep any solution contained to the thumb drive so I can learn more about ubuntu and get used to using it before I install it on the machine and start making changes that will be more difficult to correct.

Thanks for your help.

---

### Post by creator101 on 2011-11-30
Have you tried booting into a different kernel version? If not, hold down shift at the HP screen after you press the power button until the GRUB comes up. Select an older kernel and press enter.

---

### Post by drs305 on 2011-11-30
It sounds like a video driver problem. 

I know this works for Nvidia and your problem could be similar.

At the Grub menu, highlight the kernel you want to boot and press 'e' to edit the entry.

Cursor to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'. 

Press CTRL-x to boot.

If it boots, click the upper left icon (Home button) and type Additional Drivers and see if your video driver is available for installation.

---

### Post by Tanist on 2011-12-01
Clearly I did something wrong when I tried to create the image on the thumb drive.  After trying both of your suggestions I get nothing.  

I then tried to get further in the process, in the split seconds I had I finally got to a Help menu option just before the boot process would begin.  Trying the options there and then giving a text command to boot I got on several occasions the response "could not find kernel image".

I need to move back a few steps and try again.  Thanks for your help and I'm sorry if I wasted your time.  I may try to install through wubi and see what happens since my end goal is a dual boot system and I understand that I can get there later with a wubi install.

---

### Post by drs305 on 2011-12-01
You are right that it is a problem not with Ubuntu but something in the boot process/thumb drive setup that is preventing the kernel from being located.

Normally I'd recommend trying to install Boot Repair (see link in my signature line) but I guess you can't get to a LiveCD/USB Desktop to even run that. 

Bootable USB's are getting better and a bit more reliable but you are not alone in having difficulties getting them to work properly the first time around.

---

