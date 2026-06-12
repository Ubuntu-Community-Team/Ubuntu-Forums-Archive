---
title: "Samsung Chronos series 7 configuration"
date: 2012-03-18
forum: Hardware
---

### Post by miatawnt2b on 2012-03-18
I wanted to start this thread to see if anyone can add some ideas to get ubuntu working well on this laptop. I am stuck with a 29W power draw, and the battery life is awful.

Got mine (a 700z5a-so4) a few nights ago and immediately wiped and installed oneiric and a 3.2.0rc4 kernel.

to get the touchpad working properly, edit the file
/usr/share/X11/xorg.conf.d/50-synaptics.conf
and add the following lines

Option "FingerLow" "1"
Option "FingerHigh" "1"
Option "FastTaps" "1"
Option "SingleTapTimeout" "360"

also I've disabled the radeon kernel module until hybrid video is better supported.

Also used this link to get the wireless working again after the 3.2 kernel.

[http://www.mindwerks.net/2011/11/wir...12-3-2-kernel/](http://www.mindwerks.net/2011/11/wir...12-3-2-kernel/)

and some more tweaks
[http://forum.notebookreview.com/sams...nux-guide.html](http://forum.notebookreview.com/sams...nux-guide.html)

That's about all the farther I've gotten. I still have very high power usage on battery at 29W. I need to get that down a bit more.

At this point I am at a loss to go much further, I'm guessing the hardware is just too new to be well supported in Ubuntu.

If anyone has more ideas please post them here. We need a thread for the series 7... there really isn't much info out there about it.

-J

---

### Post by abaranau on 2012-03-20
Using 11.04 (don't want to upgrade to stuck with new desktop...).

I managed to get as low as 19-21 W. Thought still much more than in WIndows 7 (when idle I saw even 8W-10W with wifi on).

Another hint may be useful for someone: 
I was very annoyed with the minimal speed of the mouse pointer when using touchpad. Acceleration worked great, but when you slide finger slowly the pointer moves sooo slow! This is what helped me to get good touchpad experience (note that it seems like in newer ubuntu, with 3.2+ core specifically there's a better support for touchpad):

```

xset mouse 2 1
xinput --set-prop "12" "248" 500

```

Another issue that I faced with was unstable USB 3.0 port. Not sure it is specific for Ubuntu ("lost" HDD drive several times in Windows when disconnecting power adapter) or even it is about laptop. Don't have other USB 3.0 device to check, but saw issues with WD Passport 1TB external HDD. When I put it in USB 2.0 port it works well and stable. When it is in USB 3.0 I can loose it after some time and cannot connect until reboot (and even not all the time reboot helped). It (HDD) works well with my other laptop.. Anyone saw smth similar??

Thanks,

---

