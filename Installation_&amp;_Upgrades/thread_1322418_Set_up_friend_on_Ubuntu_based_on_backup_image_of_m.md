---
title: "Set up friend on Ubuntu based on backup image of my own machine"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Jugney on 2009-11-10
Hi all,

I spent the last two weeks getting back on Ubuntu 9.10 after a break from Linux, and have configured and tweaked my system to perfection. (The Koala is treating me very well so far!) 

Now I have a friend who is interested in going to Ubuntu, and would want much the same setup as my own. So here's the question:

I'm currently creating a partition image with Clonezilla to back mine up. Can I restore the partition image to her machine, and change the user name to be her own after the system is restored? Will that work hardware-wise? Will that work OS-wise?

Or is there another way I can back up my system and use it as a base for setting up hers?

Thanks,
Jugney

---

### Post by blueridgedog on 2009-11-10
It should work, most of the hardware "drives" are modules loaded as needed.  You could also look at remastersys, which is the product I use for doing exactly what you describe.

---

### Post by Jugney on 2009-11-10
Thanks for the reference on Remastersys. Is that working in Karmic? It was unclear from the website.

---

### Post by blueridgedog on 2009-11-11
I can't see any reason that it would not work, as it is basically using the package manager and system commands.  Try it with the program you are using first and if you are not happy, try remastersys.

---

