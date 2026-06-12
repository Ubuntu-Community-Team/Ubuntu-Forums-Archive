---
title: "[SOLVED] A bit lost for patitioning my drive"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2009-01-05
I have by mistake deleted my Vista partition, not that I will miss it, but now I want to reinstall Ubuntu using more disk. So here it's the thing, I would like to have one partition with system files and one partition with all of my documents. That way, when I upgrade Ubuntu (I like to do it with fresh installs) I can save all my things on the other partition and install in the one destined for it.

Now, I have seen several options in mount point: / and /home, among others.

I guess it's between one of these two to pick. What size should I leave for the system only partition? Is 20gb a good size?

Will the second partition be available at startup? Or I'll have to mount it every time?

---

### Post by Pumalite on 2009-01-05
20 GB is good for '/' The rest for /home leaving something for /swap at the end. /home should appear in /etc/fstab; if not; you can easily add it. /swap should be 1 GB for Desktops. 1.5 GB of your RAM for laptops if you want to hibernate.

---

### Post by arashiko28 on 2009-01-05
Ok, thanks, I will start the process now and let know the results. I always leave for swap the same amount as I have of RAM, in this case 3GB.

---

### Post by arashiko28 on 2009-01-05
It worked like a charm. There is 20GB on file system and the home folder sees 151.9GB of free space.

Thanks.

---

