---
title: "random kernel crashes d830 laptop"
date: 2008-05-14
forum: Hardware
---

### Post by BackwardsDown on 2008-05-14
I've got a Dell d830 laptop. Gutsy ran fine but Hardy keeps crashing every few hours. Sometimes the laptop locks up for a few seconds (non-moving mouse, stuttering music) and sometimes it totally locks up with the scroll- and caps-lock blinking.

Compiz enabled/disabled, no luck.
Wireless/no wireless, no luck.
Not using the touchpad but a usb-mouse, no luck.
I already have made a few changes to my xorg.conf (setting DVI to false) with no effect and I have installed the backport-modules.

Kubuntu kde4 Hardy seems to crash less, but I have also seen a kernel panic on there.

---

### Post by J1sE on 2008-05-17
I also have a Dell Latitiude D830
To me it seems like we're having the same problem. I have a crash about once a day, but some times it can go days between each crash. The symptoms I usually see is the flashing Caps and Scroll Lock. Normally this happens when there is some load on the cpu... No obvious reason or way to reproduce the crash. Often before the system hangs one or more programs crashes.

I'm wondering if there are any way to catch the stack trace while still being able to use the system as normal.

uname -a:
Linux my-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by bro on 2008-05-17
Good to see I'm not alone. I've exactly what BackwardsDown describes. Though I must say that happened to use a lan-cable instead of wireless the other day and it was gone for a few hours. I was actually considering to look for a downgrade in wireless drivers. (if anybody has a clue?). 

I've got Intel graphics by the way. 

I started a question [overhere]("http://ubuntuforums.org/showthread.php?t=796187") and got the advice to ```
dmesg | tail
``` immediately after a occurence of stuttering for a few seconds and report back. Which I didn't manage to do so far.

---

### Post by J1sE on 2008-05-17
After reading both your post once more, it came to my mind that I also had hard system hangs every few hours a while back. I believe that it got a lot better after a bios update from A10 to A11. It could be worth a try :)

---

### Post by bro on 2008-05-18
I did not have any of these problems with 7.10. Since not my bios but my OS changed version, I doubt if that woulde be the cause. Also, what does my bios do for my laptop after I booted?

---

### Post by J1sE on 2008-05-18
You're probably right... updating the bios most likely doesn't have anything to do with the crashes... it's just that I experienced far less crashes after updating. But that might just be a coincidence or that I updated some other part of my system around that time.

---

### Post by BackwardsDown on 2008-05-18
Just to give it a try I have upgraded my bios from A8 to A11. Now lets wait for the stutters and crashes :)

---

### Post by BackwardsDown on 2008-05-18
While watching a flash-video I think I got the famous stutter, dmesg | tail:

[ 4050.067421] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 4055.094547] psmouse.c: resync failed, issuing reconnect request
[ 4059.601664] input: PS/2 Mouse as /devices/virtual/input/input11
[ 4059.657146] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
niels@inoue:~$

Also, after the stutter scrolling at the right side of the touchpad does'nt work anymore.

---

### Post by bro on 2008-05-18
good that you found it. I can confirm the touchpad thing, I never connected it to this problem, but Ubuntu seemed to randomly forget my configuration (I also speeded it up because of my 1650 x 1050 screen, which it would forget.) .

---

### Post by BackwardsDown on 2008-05-18
I think I have found the exact bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189814)

Same problem with Fedora(no solution though):
[http://www.nabble.com/psmouse.c-resync-failed-td16082494.html](http://www.nabble.com/psmouse.c-resync-failed-td16082494.html)

Also the fact that it only uccures when you leave the computer for a few minutes alone (reading tekst or watching a video) and then start moving the mouse again is very recognisable for me.

edit: I got the bug again after I rebooted while reading a wikipedia article, and dmesg | tail gives me this again:
[  706.900756] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 5 bytes away.
[  708.034248] psmouse.c: resync failed, issuing reconnect request
[  710.316945] input: PS/2 Mouse as /devices/virtual/input/input11
[  710.379686] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12

---

