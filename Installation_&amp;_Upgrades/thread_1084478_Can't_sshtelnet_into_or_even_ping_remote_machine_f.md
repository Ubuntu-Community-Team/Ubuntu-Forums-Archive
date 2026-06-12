---
title: "Can't ssh/telnet into or even ping remote machine following failed update"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by infinitejones on 2009-03-02
I was doing a dist-upgrade on a remote machine - I'd connected via Remote Desktop Viewer and done sudo update-manager -d.

The upgrade seemed to hang halfway through and I had to go and hard-reset the remote machine. On restarting it's clear that something's gone wrong - it gets to the point just before the gdm login screen appears and just hangs with the pale brown background.

What I'd love to be able to do at this point is hit ctrl+alt+f3 (let's say), drop out to a command prompt and fix things from there. However, this remote machine, while it has a screen (the widescreen TV in my lounge), it doesn't have a keyboard. And I don't have a desktop keyboard in the house (long story), and I don't really want to have to go and buy one.

An ideal scenario would be if I could ssh or telnet into the machine from my laptop. But ssh and telnet give "no route to host" and ping gives "destination host unreachable".

Is there anything else I can do, without a keyboard for the remote machine?

---

### Post by kdcoetzee on 2009-03-02
Sorry but so far I can tell, you will need a keyboard and screen.

because network and ssh starts after you have logged in.

I would use a Ubuntu LiveCD, start up network and ssh on the liveCD, and mount the partitions and chroot in, and fix.

---

### Post by kdcoetzee on 2009-03-02
But if you did a dist-upgrade. and killed it, before it finished.
then there maybe other problems.

from which version did you try to upgrade ?

I would try to change /etc/apt/sources.list to the version it was one and sudo apt-get upgrade.

after you have booted up with a livecd.

---

