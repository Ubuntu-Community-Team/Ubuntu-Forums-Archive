---
title: "Synaptics touchpad problems in Hardy"
date: 2008-06-20
forum: Hardware
---

### Post by Spc on 2008-06-20
I've got a Synaptics touchpad on my Toshiba laptop and it worked perfectly in Gutsy, but in Hardy it doesn't work at all, even when I start from LiveCD. Strangely enough, it seems that it gets detected well:

$ cat /var/log/Xorg.0.log | grep "ynaptic"
(**) |-->Input Device "Synaptics Touchpad"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(--) Synaptics Touchpad touchpad found
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(--) Synaptics Touchpad touchpad found

But still it doesn't work at all, and turning it on/off by pressing Fn+F9 or in Preferences - Mouse doesn't have any effect too. Any ideas?

---

### Post by Spc on 2008-06-20
No ideas? Anybody? Bump

---

### Post by stefan.ciobaca on 2008-06-20
You are not alone:

[http://ubuntuforums.org/showthread.php?t=816026](http://ubuntuforums.org/showthread.php?t=816026)

---

### Post by Spc on 2008-06-20
No, I have a quite different problem: my touchpad works perfectly both in Windows and Ubuntu 7.10 Gutsy, but fails to work in Hardy, so it's certainly not a hardware problem.

---

### Post by stefan.ciobaca on 2008-06-20
No, you *do* have exactly the same problem. Touchpad works in 7.10 and Windows, but not in 8.04. 

The first person who complained about this didn't get the touchpad to work in Windows because it was disabled with Fn+F7 (by accident, while trying to get it to work in ubuntu -- at least that's my guess).

---

### Post by stefan.ciobaca on 2008-06-20
I solved my problem, you can check out the thread maybe you can do it too.

---

### Post by Spc on 2008-06-20
No, your solution didn't help me. BTW, I was not upgrading from Gutsy, I made a clean install.

---

### Post by gedden on 2008-06-23
I am having a similar problem so I thought I'd chime in here. In xorg.conf or whatever it's called, I believe you have to change a setting to use the touchpad applet in the preferences menu. So thats what I'm looking for, It might be similar . I am using a compaq armada m300 with a fresh install. I had done this in the past, so I'm looking with search terms like laptop mode.

---

### Post by normanecker on 2008-06-23
what model toshiba are you using? i have a toshiba p100 with hardy 8.04 and synaptics touchpad worked fine from live cd install.

---

