---
title: "Security of Ubuntu installed in XP"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by albanach on 2009-09-03
If I install Ubuntu within XP, will the computer be vulnerable to viruses, malware, etc. just like XP?

At present, I have Ubuntu and XP installed on seperate partitions and Ubuntu runs with no virus checker; would this still be possible with Ubuntu installed within XP?

Thank you

---

### Post by presence1960 on 2009-09-03
why would you want to install Ubuntu "in XP" with wubi when you already have it on a separate partition? Wubi is not meant to be a permamnent OS. it is meant to be a test where the user can "try" Ubuntu before partitioning their hard disk. You already have that done.

Don't believe me see:
[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by albanach on 2009-09-03
Thank you for the quick reply.  

I was under the impression that running Ubuntu as a virtual machine within XP was a permanent option.  The reason I asked was because a friend wants to try Ubuntu and lives too far away for me to keep an eye on things in the early days.  


Thanks again.

---

### Post by presence1960 on 2009-09-03
> **albanach said:**
> Thank you for the quick reply.  

I was under the impression that running Ubuntu as a virtual machine within XP was a permanent option.  The reason I asked was because a friend wants to try Ubuntu and lives too far away for me to keep an eye on things in the early days.  


Thanks again.

Read the links I posted. Wubi is not a virtual machine. But since wubi is installed within windows filesystem it is subject to performance slow down due to windows fragmentation.

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

from the above link:

While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1][COLOR="Red"] The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks)[/COLOR]

Note the red text.

for some reason the link does not work. But if you do a google search of wubi it is the third entry down - wubi (installer) - wikipedia

---

### Post by albanach on 2009-09-03
Thanks for the info. The Wubi option might be best for my friend to try Ubuntu to see how he gets on with it.

---

