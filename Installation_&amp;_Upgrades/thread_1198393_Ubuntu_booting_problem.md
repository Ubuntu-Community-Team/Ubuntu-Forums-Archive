---
title: "Ubuntu booting problem"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by susanta on 2009-06-27
I had window xp and ubuntu in my system.Iformatted window with ubuntu,now i have two nos of ubuntu during booting.Kindly help mp so that i can get rid of the above problem.THANK YOU

---

### Post by monkeyking on 2009-06-27
If you had ubuntu on one partition,
and then you installed another ubuntu on another partition.

Then you effectivly have 2 ubuntu,
so you should decide which one to delete(old or new).

Check which one by selecting the right one at boot time (grup options).

When you are sure delete the item in /boot/grub/menu.lst

And if you can still boot,
consider using gparted for the format of the obsolete ubuntu.

good luck

---

### Post by cariboo on 2009-06-27
Another thing you may have, if you didn't install Ubuntu a second time is, there may have been a kernel update, and you would have the old kernel and the new kernel listed in grub.

---

