---
title: "Using vista partition editor to resize ubuntu partition?"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by lbmounse on 2009-02-19
Is it safe to use the vista partition editor to resize the ubuntu partition?
If not, how can I resise the partition to claim free space gained by shrinking the vista partition?

When I installed ubuntu, the vista partition editor would only let me resize the vista partition by 15 GB.  Now, it is saying I can have 9 GB more.  If I can, I will just keep whittling down the vista partition, and give it to ubuntu.

---

### Post by whoop on 2009-02-19
I would advise booting up a live-cd of ubuntu and type this in a terminal:
```

gksudo gparted

```
It's a good partition editor.

---

### Post by caljohnsmith on 2009-02-19
Definitely don't use the Vista Disk Management to resize the Ubuntu partition, because Vista has no knowledge of linux file systems. If you boot your Live CD, you can use gparted (System > Admin > Partition Editor) to expand the Ubuntu partition once you shrink the Vista partition. Good luck and let me know how it goes.

---

### Post by glotz on 2009-02-19
First, some instructions suggest you first defragment the windoze partition (using the windoze tool.) Then use the windoze partitioner to shrink the windoze partition. Then, since you have such an old version (6.06) it might be the best idea to get the latest version of gparted. (from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) , click the live link in the upper right corner.) Once you get the file, insert an empty cd or a cd-rw disk and right click the iso file > write. Then boot off the gparted CD and enlarge the Ubuntu partition with it.

---

### Post by binbash on 2009-02-19
Download Gparted live CD and burn it to a CD.You will need it.

---

### Post by Therion on 2009-02-19
> **binbash said:**
> Download Gparted live CD and burn it to a CD.You will need it.
Yep.  If not today, someday.  Just do it.  It's an essential tool for every 'buntu-ist.

---

### Post by lbmounse on 2009-02-25
Ok, so the windows partitioner is telling me "Access Denied" when trying to shrink the partition.

Any suggestions?

---

### Post by Herman on 2009-02-26
I agree with what all of the previous posters have already told you, don't use the Windows partitioner.

Use GParted or any good 'Parted based partitioner and stick with it, don't change brands.
An up to date version of GParted is recommended. 

If GParted won't look at your NTFS partition, you might need to run CHKDSK on it from a Windows Repair Disc first, and it is also recommended to run CHKDSK again afterwards, (refer to GParted's documentation).

Regards, Herman :p

---

### Post by StephenOK on 2009-02-26
> **Therion said:**
> Yep.  If not today, someday.  Just do it.  It's an essential tool for every 'buntu-ist.

Yup. Gparted is a great partitioner, and its very easy to use.

---

