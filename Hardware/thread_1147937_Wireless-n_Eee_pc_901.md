---
title: "Wireless-n Eee pc 901"
date: 2009-05-03
forum: Hardware
---

### Post by l4mb on 2009-05-03
Hey, I recently installed Jaunty on my Eee pc 901. My problem is that I can't seem to connect at wireless-n speeds. The signal strength is at 100% and it still says I am connected at 54mpbs. Before I blew away wimblows it was connected at wireless-n speeds. Any help would be appreciated. The driver currently in use is rt2860 under jaunty 32-bit.

---

### Post by Menthu_Rae on 2009-06-08
Hey mate,

I beleive it is an "issue" with the rt2860 driver/module that ships with Jaunty, which is version 1.8.0.0.

Additionally with this version of the driver/module, you may find you can't connect to some WPA/WPA2 networks. :(

The good news is that there is a fix, but it involves a bit of fiddling. If you're not confident, I recommend you don't touch it and just wait until a proper fix is released.

You can find more details here (the bottom 2 posts relate to Wireless N speeds):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022)

and more specifically this post here is how to load the alternate driver:

[http://ubuntuforums.org/showpost.php?p=7069234&postcount=7](http://ubuntuforums.org/showpost.php?p=7069234&postcount=7)

I'm about to have a fiddle and see if I can get Wireless N speeds working on my EeePC 901 given the instructions in that post above. I'll post back if I do. :D

_EDIT:_ Reverting back to 1.7.1.1 driver didn't fix my Wireless N speed issue... router is a Billion 7800n. I tried different modes (g+n, n only), different channel widths (20mhz, 20/40mhz) and different channel numbers (7, auto) - none helped :( boo!

---

