---
title: "[SOLVED] 7600GS Driver issues."
date: 2009-01-09
forum: Hardware
---

### Post by RhysTheNewGuy on 2009-01-09
Hi, im having trouble installing the correct drivers for my 7600 GS 512mb GeForce card, I have tried many things, even the official nvidia.com driver

download, ctrl-f2, login, sudo /etc/init.d/gdm stop, cd Desktop(where the file is) then i sh the file.. install it all.. and reboot. despite the many times I have done this, ubuntu still tries to boot up in low graphics mode.. any suggestions?

I suspect it will be to do with my xorg.conf but im not too sure what's wrong with it.

Please respond - thanks.

btw, running 8.10 Ubuntu.

---

### Post by RhysTheNewGuy on 2009-01-10
ah, solved now, my problem was I was rebooting to early, was meant to start gdm again - used this howto [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)
even though it says 8.04 it works with 8.10

---

