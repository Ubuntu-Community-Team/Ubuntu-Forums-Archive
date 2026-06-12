---
title: "[SOLVED] help on partitioning"
date: 2008-11-12
forum: General Help
---

### Post by thehellboy on 2008-11-12
i'm a new bie to linux.. i want to install ubuntu in my acer 5052 laptop.. can any one tell me what are the partitions, their minimum size and mount points, i need to create to install ubuntu..
thanks in advance..

---

### Post by Shwefty on 2008-11-12
Are you dual-booting?  I checked up on the Acer Aspire 5052 for those who post below me, 120 GB hd.

---

### Post by jimmy the saint on 2008-11-12
If you are a total newb, just let the installer decide for you.
If not, I would do something like 
300MB -- Boot
12GB -- / (root)
1.5xRam -- Swap (for hibernate)
the rest as /home

That way, when you upgrade, your home directory is untouched

---

### Post by thehellboy on 2008-11-12
no im not dual booting.. installing ubuntu alone

---

### Post by jimmy the saint on 2008-11-12
Then the scheme I laid out should work fine.  If you do not plan to hibernate, you can get away with a lot less swap space.  These days, it is hardly ever (if ever) used.  But it is neccessary to have more swap than you have ram if you want to use the hibernate function.

---

### Post by thehellboy on 2008-11-12
jimmy.. thx 4 ur scheme..more over the 8.04 amd 64 live cd i burnt was not bootin in my laptop.. it got stuck on the load screen where progress bar appears.. any help??

---

