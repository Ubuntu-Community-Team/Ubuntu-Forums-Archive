---
title: "Weird problem with touchpad"
date: 2009-11-13
forum: Hardware
---

### Post by nille86 on 2009-11-13
I just installed ubuntu 9.10 1 hour ago and the problem started with the installer. I figured it was just temporary but when i got ubuntu up and running the problem is still there. 

The pad works fine, the problem is with the buttons. When i press the left button the window i have focused scrolls up and when i press the right button the window scrolls down. If i hold CTRL and click on a link(in firefox) i open up a new tab AND increase the textsize.

The problem isnt just with firefox though, if i have a terminal open that has a scrollbar the same thing happens. 

When i try to move a window i can only move it for 0.5 seconds and then it stops and just lets go of the window.

I installed ubuntu instead of LFS(linuxfromscratch) and the touchpad was working fine in LFS.

Hope someone can help me as I havent found anything useful from googling.

I updated ALL my packages to the most recent versions but still no luck.

---

### Post by fidelandche on 2009-11-13
Have you clicked on system=pref=mouse? and adjusted things there?

---

### Post by nille86 on 2009-11-13
Yes i have.. but all I find there is three tabs that dont do very much good to me.. I have tried to disable and enable most of the stuff there but it still doesnt work.

---

### Post by grimeywelsh on 2009-11-13
Ubuntu geek has a write up on this issue.  
[http://www.ubuntugeek.com/howto-fix-touchpad-issues-after-karmic-upgrade.html](http://www.ubuntugeek.com/howto-fix-touchpad-issues-after-karmic-upgrade.html)

Hopefully this will help

---

### Post by nille86 on 2009-11-13
Nope, im afraid not. 

I am running the latest kernel there is and there are no errors reported from dmesg. Lsmod shows the psmouse is loaded aswell.

There is one thing that is bugging me and that is:

nille@C1:~$ dmesg | grep mouse
[    1.082529] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.114074] mice: PS/2 mouse device common for all mice

I have tried to disable the macintosh emulation by adding the file /etc/hal/fdi/preprobe/10-blacklist.fdi

<?xml version="1.0" encoding="UTF-8"?>

<!-- 15/12/2008 by BJ
*Match* devices you want to blacklist and *merge* info.ignore to true
Get the necessary info to match with hal-device
-->

<deviceinfo version="0.2">
<device>
<match key="info.category" contains="input">
<match key="input.product" contains="Macintosh">
<merge key="info.ignore" type="bool">true</merge>
</match>
</match>
</device>
</deviceinfo>

But i dont know if i have succeeded.

---

### Post by nille86 on 2009-11-14
Running xev and clicking left button and right button shows some disturbing stuff:

Pressing left button quickly and releasing:
ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 1941709, (175,176), root:(178,224),
    state 0x0, button 4, same_screen YES

ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 1941769, (175,176), root:(178,224),
    state 0x800, button 1, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 1941769, (175,176), root:(178,224),
    state 0x900, button 4, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 1941784, (175,176), root:(178,224),
    state 0x100, button 1, same_screen YES

Pressing right button quickly and releasing:
ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2057219, (172,176), root:(175,224),
    state 0x0, button 5, same_screen YES

ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2057289, (172,176), root:(175,224),
    state 0x1000, button 3, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2057289, (172,176), root:(175,224),
    state 0x1400, button 5, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2057294, (172,176), root:(175,224),
    state 0x400, button 3, same_screen YES

If i keep pressing a mouse-button xev will just print:
ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2231311, (172,171), root:(175,219),
    state 0x100, button 4, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x5e, subw 0x0, time 2231391, (172,171), root:(175,219),
    state 0x900, button 1, same_screen YES

until i release the button.


Clearly it detects two buttons being clicked. Can anyone else try this and post their output??

---

### Post by ptn on 2009-11-18
The Ubuntu Geek stuff did not work for me.

xev shows coherent output, a ButtonPress and then a ButtonRelease.

---

