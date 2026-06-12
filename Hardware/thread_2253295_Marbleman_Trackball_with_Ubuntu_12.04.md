---
title: "Marbleman Trackball with Ubuntu 12.04"
date: 2014-11-18
forum: Hardware
---

### Post by manthony121 on 2014-11-18
Does anyone else use a wired, USB, Logitech Marbleman trackball with your linux desktop?  I do, and it generally works well, but there is one problem that I have not been able to figure out.  If the ball is not moved for about 30 seconds, it seems to go into a sleep state.  Small movements of the ball have no effect.  Pressing any of the 4 buttons is instantly recognized.

Has anyone else seen this behavior?  I am trying to figure out if it is in the Marbleman firmware, or the USB driver, or at a level even higher than that.

---

### Post by manthony121 on 2014-12-02
The problem was with a package I had installed called "powernap".  I was using this computer to experiment with waking other computers on the network for backing them up, then shutting them down again.  Powernap includes a daemon that puts usb devices on the local computer to sleep.  Using the command, "sudo powernap-action --disable usb_autosuspend" has elminating the sleeping mouse problem.

---

