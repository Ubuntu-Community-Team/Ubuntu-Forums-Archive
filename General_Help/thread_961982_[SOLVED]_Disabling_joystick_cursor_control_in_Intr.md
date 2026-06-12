---
title: "[SOLVED] Disabling joystick cursor control in Intrepid"
date: 2008-10-28
forum: General Help
---

### Post by nitrousoxide82 on 2008-10-28
I've just upgraded to Intrepid via the net (over a gig of stuff downloaded) and have just noticed it automatically uses my joystick (a PlayStation 2 pad connected via USB) to control the X mouse cursor. I understand that this is due to the fact Kubuntu is using HAL to determine input devices for X (instead of xorg.conf) and that HAL has detected my joystick and decided that X can use it. 
Problem is, I can't use my joystick for what I primarily want to use it for (that is, games) as it seems that all of the joystick input is being directed to X and so other programs (this includes the Joystick control panel item in KDE, or even jstest run from Konsole) can't seem to receive input from the joystick.

Any input is greatly appreciated (no pun intended).

---

### Post by bigfox on 2008-10-28
I am having this problem as well.  As far as I can tell it effects only 64 bit installs.  None of my 32 bit systems have this problem.

It effects both Ubuntu and Kubuntu.

The problem effects all joysticks and gamepads with an X and Y axis.

I have already submitted a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/288800](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/288800)

---

### Post by jordan420 on 2008-10-30
> **bigfox said:**
> I am having this problem as well.  As far as I can tell it effects only 64 bit installs.  None of my 32 bit systems have this problem.

It effects both Ubuntu and Kubuntu.

The problem effects all joysticks and gamepads with an X and Y axis.

I have already submitted a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/288800](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/288800)
Well i can confirm that this is a problem. on 64bit. you guys nailed it. i wonder if it will be fixed in the main release..

---

### Post by zinchalk on 2008-10-30
I am running intrepid 32bit update from 8.04. I also am having the same problems so it might be effecting both platforms.

---

### Post by bigfox on 2008-10-30
Here is another bug report describing the same problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203)

If more people go there and mark at the top that it effects them as well, maybe they will fix it.

---

### Post by bigfox on 2008-10-30
I have tested it on a number of 32 bit installs of intrepid, but not since it has gone final release.

I will test it on 32 bit again.  Its depressing to hear that this bug might be getting worse.

---

### Post by nitrousoxide82 on 2008-10-31
> **bigfox said:**
> Here is another bug report describing the same problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203)

If more people go there and mark at the top that it effects them as well, maybe they will fix it.

I followed links from there and found a fixed xserver-xorg-input-evdev package. Installed it, and that fixed my problem. Hope the fix makes it into the Ubuntu repositories soon. Thanks!

---

