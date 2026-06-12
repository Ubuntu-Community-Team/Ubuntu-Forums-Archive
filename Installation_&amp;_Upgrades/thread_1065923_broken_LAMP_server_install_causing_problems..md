---
title: "broken LAMP server install causing problems."
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by mistafeesh on 2009-02-10
Hi, not sure where to post this but here goes...

I recently installed Ubuntu using Wubi. All went smoothly, but then I tried to install LAMP server environment (for testing sites) with the command
sudo tasksel install lamp-server
Which didn't work properly. When I tried to install something else, I got a message telling me to run the command
sudo dpkg --configure -a
which I did but I got the error message
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
when I tried the LAMP install again it wouldn't work.

any ideas?

also, probably unrelated, but when I try to install something from a .deb package, I keep getting a message saying that it's the wrong platform i386 even though I've got an Intel processor it's a HP 6720s laptop if that helps)

Thanks

Dan

---

