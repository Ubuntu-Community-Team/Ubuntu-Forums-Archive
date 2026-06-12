---
title: "don't see the option to create a partition on install"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by anico on 2009-07-21
Hello,
i'm trying to install ubuntu 9.04 on a Compaq Presario X1000 (old machine).. for some reason, it's not showing me the option to select the size of the partition during the installation - only the one where it selects the entire disk or the manual one (advanced). I used the live CD to open up Gparted but when i tried to resize the disk.. it only let me resize it by 8MB. I have about 40GB free on this computer so i don't know why it's not letting me create a larger Free Space for ubuntu to use it.
Thanks a lot!

---

### Post by merlinus on 2009-07-21
What other os are you running?

---

### Post by anico on 2009-07-21
I'm running windows XP, i want to make a dual boot. I've done this before on vista, so i'm guessing it's an XP problem?

---

### Post by merlinus on 2009-07-21
Be sure to defrag windows several times, and you also may have to disable the paging file as well.  It usually takes up lots of room at the end of the partition.  The option is probably somewhere in system tools.

Then restart and delete pagefile.sys, defrag, and then try resizing with gparted.

---

### Post by anico on 2009-07-21
i did refrag twice but i'll give it a go again! and disable the paging file.
thanks for your advice

---

### Post by anico on 2009-07-21
ugh.. no luck.. i still can't seem to create a partition for ubuntu.

---

### Post by merlinus on 2009-07-21
Can you post a screenshot from gparted?

---

### Post by anico on 2009-07-21
here are the screenshots of Gparted...should i consider installing ubuntu within windows? i see it's an option in 9.04 but is it worth it?

---

### Post by merlinus on 2009-07-21
I assume that sda1 is unmounted...

Also, there appears to be some kind of warning icon on it.

---

### Post by merlinus on 2009-07-21
I assume that sda1 is unmounted...

Also, there appears to be some kind of warning icon on it.

You might try gparted live, which is a later version than on the ubuntu install disk.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Also, if you rightclick on sda1, there is an information selection which may help.

---

