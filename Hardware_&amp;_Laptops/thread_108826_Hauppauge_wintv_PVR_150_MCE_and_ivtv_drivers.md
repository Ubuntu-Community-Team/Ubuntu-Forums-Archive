---
title: "Hauppauge wintv PVR 150 MCE and ivtv drivers"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by ShadowRage on 2005-12-27
I've had to custom compile the latest ivtv, install the firmware, etc, the card initializes, and sometimes (read: sometimes) can be accessed, but only with the ivtv utils.

Any tv viewers that ACTUALLY work with these cards? other than the standard response of "oh, those are good cards cuz they work in linux lol"
because as far as I'm seeing atn, they work as in some hardware and utils can communicate with them.
I get a little mpeg II stream when I cat /dev/video0

but tvtime not xawtv can use the card.

So, what are some good programs to use?

also, do not mention mythtv as it is a PVR environment more than a tv viewer, I just need a simple tv viewer.

---

### Post by bneuro1 on 2005-12-27
I don't know if those program work with your card but you can try

Zapping is a TV viewer for the Gnome at [http://zapping.sourceforge.net/cgi-bin/view](http://zapping.sourceforge.net/cgi-bin/view)

kdetv is a KDE application to watch TV on the desktop at
[http://www.kdetv.org](http://www.kdetv.org)

XdTV is a software that allows you to watch TV at
[http://xawdecode.sourceforge.net/](http://xawdecode.sourceforge.net/)

---

### Post by ShadowRage on 2006-01-18
turns out using vlc in pvr mode is the only way to go, the apps you posted are all v4l1, and outdated in the respect they're not v4l compatible, they also dont play nice with pvr cards as they dump mpeg streams.

---

### Post by artfart91 on 2008-07-06
> **ShadowRage said:**
> turns out using vlc in pvr mode is the only way to go, the apps you posted are all v4l1, and outdated in the respect they're not v4l compatible, they also dont play nice with pvr cards as they dump mpeg streams.

how do you change channels in vlc?

---

