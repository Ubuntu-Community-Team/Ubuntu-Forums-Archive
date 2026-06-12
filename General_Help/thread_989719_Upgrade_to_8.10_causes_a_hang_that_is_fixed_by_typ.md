---
title: "Upgrade to 8.10 causes a hang that is fixed by typing exit!  Need permanent fix!"
date: 2008-11-21
forum: General Help
---

### Post by ryanthemadone on 2008-11-21
Hi everyone,

I just upgraded to 8.10, everything seemed to go ok, however when I boot, the system hangs at the following point;

[   39.528541] raid1: raid set md0 active with 2 out of 2 mirrors

If I hit enter I'm presented with an initramfs prompt and if I just type 'exit' the system continues and boots as normal.  As the server is in a difficult to reach location this is less than ideal.

Some background, I use LILO to boot the system because I had trouble with GRUB not liking my configuration back in 7.04.  I have a simple software raid 1 with LVM over the top, root and all that exists within this.

Your helps is much appreciated kind people,

Ryan. :KS

---

### Post by ryanthemadone on 2008-11-22
Have I posted this in the wrong place perhaps?

---

