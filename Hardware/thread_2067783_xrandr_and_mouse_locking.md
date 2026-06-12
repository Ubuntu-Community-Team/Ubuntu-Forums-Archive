---
title: "xrandr and mouse locking"
date: 2012-10-07
forum: Hardware
---

### Post by DarkAz on 2012-10-07
Greetings.

I'm currently using an Acer Aspire One ZG5 with a Xubuntu 12.04 install, and am having some problems with xrandr. I'm using it to set up a 1280x720 (scaled) resolution from the native 1024x600, which by itself works fine but after the resolution change, the mouse stays "locked" in a box the same size of my native resolution.

This is apparently a bug as analysed [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319"), and a patch was made available [here]("https://launchpad.net/~mdeslaur/+archive/testing/+build/3734134"). Sadly I can't for the life of me figure out how to apply said patch, can anyone give me a hand? Thanks in advance to all who reply.

---

### Post by dodo3773 on 2012-10-07
The second link you supplied has pre-built binary .deb files. Just download and install them. Are you not running 32 bit (i386)?

---

### Post by DarkAz on 2012-10-07
Yes, it's a 32bit install. I was unsure if I had to install all of the .deb's or just one in specific.

---

### Post by dodo3773 on 2012-10-07
> **DarkAz said:**
> Yes, it's a 32bit install. I was unsure if I had to install all of the .deb's or just one in specific.

Looks like it may be built as a meta-package. So, I guess you could install them all or you can look at the first link and scroll down to the part where the ppa is discussed and try it that way. Just make note of the old package versions so you can revert if you need to.

---

### Post by DarkAz on 2012-10-07
Well, went in guns blazing and installed everything. Good part is it works, bad part is it bugged both rotating the screen and the touchpad.

However, that is beyond the point of this post. Thanks a bunch dodo3773.

---

### Post by dodo3773 on 2012-10-07
> **DarkAz said:**
> Well, went in guns blazing and installed everything. Good part is it works, bad part is it bugged both rotating the screen and the touchpad.

However, that is beyond the point of this post. Thanks a bunch dodo3773.

You're welcome. Hope you sort out the bugs caused by the bug fixes :P Also, look through that thread it seems that these fixes are implemented to work on a certain kernel version if I recall correctly. You may want to keep digging

---

