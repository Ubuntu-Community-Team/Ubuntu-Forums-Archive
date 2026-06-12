---
title: "&quot;Guided - use the largest continuous space&quot;, question."
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by Nitrius on 2009-01-09
I have a 500GB WDC disk. I got vista and two other partition on it. Vista in the start(150GB), one 50GB in the middle, and the rest in the end. The 50GB in the middle is unallocated, and there is where i want to install Ubuntu.

So i tried to select the "Guided - use the largest continuous space" but the after image of the disk shows the whole disk as blue and 100% Ubuntu 8.10, so i wonder if i proceed, will i lose everything on my disk then? So it seems that this options is a bit bugged? If so, how do i go about using the manual way? I still want to use this 50GB i've left over in the middle of the disk ofc.

And yes, am 100% sure that the 50GB in the middle is unallocated.

Edit: About the Manual way, what am wondering, if that's the way i should install, i need a /(root) partition, and a swap too maybe?(Got 4GB of RAM, and am trying to install Ubuntu x64). How much space out of the 50GB should the root and swap take? And what else should i make?

---

### Post by mikewhatever on 2009-01-10
I would just allocate all 50 GB to root. With 4 GB of RAM, you'll likely never get to use any swap.

---

### Post by Nitrius on 2009-01-10
Did it through Manual, and made / (root) 15GB, /swap 1GB and /home 34GB. / (root) was set to primary, and the two other was set to logical. And so far everything is working great.

---

