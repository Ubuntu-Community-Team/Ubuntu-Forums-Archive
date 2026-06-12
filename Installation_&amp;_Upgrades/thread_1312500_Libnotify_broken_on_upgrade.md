---
title: "Libnotify broken on upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by 0olong on 2009-11-03
Since upgrading to Karmic yesterday (which otherwise went very well) the libnotify popups are badly broken - they're just showing as rectangles of colour with odd vertical lines down them every few pixels. Reinstalling the libnotify package didn't help, and nor did adding libnotify-dev.

Has anyone else had this problem? What sort of details should I post to help debug this?

---

### Post by prince.buster on 2009-11-21
I have this problem.

The notification boxes show up with no text and all distorted.

A similar effect happens to title bars and windows when I have desktop effects enabled. 

I'm using an IBM X31 and I know that the graphics-card driver is incomplete and buggy. But the notification popups worked fine in 9.04 - perhaps the rendering been changed to hardware?

Is there a way we can just disable them?

---

### Post by 0olong on 2009-12-18
I see this bug seems to have been reported at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582) and [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/462467/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/462467/)

Seems to be a problem with the ATI driver, which can be fixed at teh expense of a great performance hit by switching to EXA acceleration - which doesn't *quite* seem worth it just so I can see libnotify popups (and gnome-system-monitor).

*sigh*

---

