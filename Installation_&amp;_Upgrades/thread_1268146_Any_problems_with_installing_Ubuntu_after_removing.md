---
title: "Any problems with installing Ubuntu after removing Windows XP?"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by utkarsh2012 on 2009-09-16
I am Planning to replace Windows XP over Ubuntu, need some feedback, when I last installed Mandrake, 4 years ago, my D and E drive vanished from My Computer! Maybe due to file system incompatibility, it was FAT32 at that time.

Is this problem still there? or I just need to 

1. put in my Ubuntu CD
2. overwrite my C drive (which will be formatted) and install ubuntu after removing win
3. Open my computer in ubuntu and see my D and E drives :lolflag:

Note: D and E are physical partition of my HDD.

---

### Post by louieb on 2009-09-16
Installation is quite flexible if you use the manual partitioning option.  Less so if you use the automatic or guided options. 

Depends is c: on a hdd by itself and d: - e: on a 2nd drive? if so the one of the automatic options would work. If c: is on the same hdd with d: and or e: you will need to use manual partitioning.

---

### Post by utkarsh2012 on 2009-09-16
Hey! Thanks for the reply!

So, here is my computer's HDD division: I have 1 HDD of 160GB capacity.

C: 40GB
D: 60GB 
E: 60GB

Therefore, to answer your question, C, D and E drives are on the _**SAME HDD**_.

So, as per your reply, I have to do manual partitioning;

> If c: is on the same hdd with d: and or e: you will need to use manual partitioning.

1. Will the installation process prompt me for the automatic and manual partitioning?
2. is manual partitioning tedious?
3. Data loss risk involved? (since all my work is on D drive! can't afford to loose it or loss to access to them for more than a day or two!)

Thanks!

---

### Post by raymondh on 2009-09-16
> **utkarsh2012 said:**
> Hey! Thanks for the reply!

So, here is my computer's HDD division: I have 1 HDD of 160GB capacity.

C: 40GB
D: 60GB 
E: 60GB

Therefore, to answer your question, C, D and E drives are on the _**SAME HDD**_.

So, as per your reply, I have to do manual partitioning;



1. Will the installation process prompt me for the automatic and manual partitioning?
2. is manual partitioning tedious?
3. Data loss risk involved? (since all my work is on D drive! can't afford to loose it or loss to access to them for more than a day or two!)

Thanks!

The risk of data loss is always there.  I suggest you back-up those files someplace else in the meantime.

Manual partitioning is not tedious.  It can be a challenge if you are not familiar with the process, the terminologies, etc.

You have to select manual partitioning.  You do so in step 4.  You highlight the appropriate partition, you EDIT, you USE, you select the mountpoint (root ... (/) in this case, and you choose the format you prefer to use.

[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html)

You may have to manually mount the other 2 partitions.  However, I have had my ubuntu automatically read/write such partitions ... hence the word "may".  Let's work on that after a successfull install.

1.  Back-up your files.
2.  Try the liveCD in live session.  It gives you a chance to see how your system works with ubuntu.  It will also allow you to see the AUTOMOUNT (for lack of a better word) by going to places.
3.  When ready, DEFRAG windows (C;drive).  2x if you have the time.

Good luck.

---

### Post by utkarsh2012 on 2009-09-16
wow....great reply!

Thanks for the help man! Gonna try it out this weekend!

Cheers!

---

