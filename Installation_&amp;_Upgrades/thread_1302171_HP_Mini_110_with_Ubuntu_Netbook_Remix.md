---
title: "HP Mini 110 with Ubuntu Netbook Remix"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by BryanJones on 2009-10-26
Hi all,

So, I got a snazzy new HP Mini 110-1081TU, and got it with Linux since... well, I'm sure I don't need to say much there.

But, I found the HP MIE OS to be rather... locked down, for my tastes. I like to be able to upgrade Firefox to v3 without losing my hair. So, I looked around, and found the Ubuntu Netbook Remix.

It's gone rather well, but the one thing I've found that doesn't work is sound. I've tried all sorts of fixes from yonder Google to get it working, but nothing's worked. All the ALSA config/updates and such, and the last one was something involving copying the kernel from the MIE files and running on that.

The kernel thing very didn't work, it went to the HP boot screen and got stuck there...

So, I'm on a clean install of UNR now, and back to comfortably soundless. Any help as to how to fix?

---

### Post by zeroseven0183 on 2009-10-26
It is a known issue in version 9.04 as per  [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks") (see your netbook model)

What version of UNR did you install?

---

### Post by BryanJones on 2009-10-26
9.04... And for some reason, I could swear I'd tried the fix posted on the link you gave, except that time, it didn't work, and this time, it did... It seems to be that the config edit it gives is what lets you have the 'surround' option show up in volume control, which is what fixed it...

Thanks!

---

### Post by BryanJones on 2009-10-27
Just as a reference for anyone else getting this problem, the steps given by
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175)
work just fine for me, though it mutes the Surround channel by default for some reason.
So, a little script of 'amixer set Surround unmute' set to run on startup is a handy fix for that.

---

