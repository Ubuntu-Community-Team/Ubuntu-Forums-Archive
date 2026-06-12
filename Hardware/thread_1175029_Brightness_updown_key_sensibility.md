---
title: "Brightness up/down key sensibility"
date: 2009-05-31
forum: Hardware
---

### Post by PatrickVogeli on 2009-05-31
Hi there!

Since having installed ubuntu jaunty, I'm having a small problem: the brightness up and brightness down keys are working, but not the way they're supposed to. My LCD can do steps 0 up to 7, but pressing the brightness down key, instead of doing 7-6-5-4-3-2-1-0 will do 7-5-3-1-0.

Pressing the up key, will output 0-2-4-6-7.

That's not the only problem: sometimes, pressing the bright up key will generate and acpi event bright up AND bright down, so the brightness doesn't change (in fact it does, since you can see how it first goes up and the down again)

If I unload the video module, the steps work fine, but then of course I loose the screen acpi dimming when idle.

It worked correctly in Ubuntu Hardy and Intrepid, but it also didn't in Debian 5.0.1. I guess it's a bug somewhere upstream, maybe hal? I highly doubt it's something kernel related, since a vanilla kernel throws the same error (tested 29, 29.1, .2, .3 and .30-rc7).

A bug report is filled here: [https://bugs.launchpad.net/ubuntu/+bug/352699](https://bugs.launchpad.net/ubuntu/+bug/352699)

Waiting for you comments!

---

### Post by PatrickVogeli on 2009-06-04
Hi there,

just a quick UP! to say the problem is solved, this time thanks to the great gentoo wiki.

Create the file /etc/modprobe.d/video.conf and paste in the following: options video brightness_switch_enabled=0

save, reload the module and it's working as it always has!

---

