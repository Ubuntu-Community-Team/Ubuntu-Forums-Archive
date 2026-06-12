---
title: "[SOLVED] Help growing partition"
date: 2008-09-07
forum: General Help
---

### Post by dazzlindonna on 2008-09-07
Ok, i've got some unallocated space to the left of the partition that I want to expand.  In the screenshot below, you'll see that there is 51.73 G unallocated and just to the right of that is sda5 with 46.79 G.  I want to grow sda5 so that it includes the 51 Gigs of unallocated space to the left of it.

I know I need to use gparted from live cd.
I assume I just highlight sda5, right-click, choose Resize/Move, and then....

That's the point I get lost on.  What next?  Does it just automatically know to use that unallocated space to the left?

I'm afraid to mess this up, so I'd rather ask first.  Thanks for any help.  Here's the pic of my partitions...

[[IMG]http://img141.imageshack.us/img141/1265/partitionsrm2.th.png[/IMG]](http://img141.imageshack.us/my.php?image=partitionsrm2.png)

---

### Post by forger on 2008-09-07
I'll say it in front that I am not sure, just speculating.
I think that first you have to expand the extended /dev/sda3 (which includes logical sda5) and then expand /dev/sda5

I'm not sure if it's even possible! It would probably be better to backup to another hard drive before you attempt to do anything..:\

---

### Post by dazzlindonna on 2008-09-07
I do have a backup on an external drive, so not too worried, but I'd still prefer to do it right the first time, and not have to depend upon the backup.

Anyone who is sure?

---

### Post by Shazaam on 2008-09-07
You first have to resize sda3 (Extended partition) to the left. Then you can resize sda5. When you get to the resize window at the top is a box with arrows on either side. Move the left side arrow left on both sda3 and sda5.
It takes longer but do each operation one at a time (safer).

---

### Post by dazzlindonna on 2008-09-08
That worked perfectly. I did have to right-click the swap partition first, and turn swapoff, to get rid of the locks, but other than that, it went smoothly.  5 hours worth of smooth, but smooth nevertheless. Thanks!

---

