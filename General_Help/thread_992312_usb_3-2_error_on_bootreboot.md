---
title: "usb 3-2 error on boot/reboot"
date: 2008-11-24
forum: General Help
---

### Post by Vire on 2008-11-24
I only recently installed Ubuntu 8.10 and originally it ran quite well, well, for about a day. I was (as a complete noob) having issues finding my C: drive (I've found it now) and as a result added a line to my fstab in hopes of fixing it. I later removed the same line when it solved nothing, but afterwards (or around the same time anyway, I'm uncertain if the fstab being edited and this error are related) I started getting this error when I boot Ubuntu up or reboot. It happens before the you login to Ubuntu though. 

Here's the error;
(these numbers seem to be random, the error repeats with different sets)
[123.602397] usb 2-3: Device descriptor read/64, error -110


This repeats about a dozen times, slowly, and makes me wait about 5-10 minutes for Ubuntu to load up (or close down).

I searched and found no similar topics on this forum, but i did manage to find something similar [here]("https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/88746").

However, my USB 2.0 works fine, so I don't really think it's a problem with that.

---

