---
title: "Resizing Linux partition to the left"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by evasquez924 on 2009-08-24
Hi,

I have a computer with one Harddrive divided into 5 partitions (+some free space).

From left to right it looks something like this:
1. Acer Partition
2. Windows XP (C Disk)
3. Windows XP (D Disk)
X. Free Space
4. Linux
5. Linux (Swap)

What I want to do, is to expand the 4. partition (the Linux partiton), to the left, using the free space, but I can't find out how. I've tried with GParted, but I can't resize the Linux partition, because I'm using it when I'm in Linux. I also tried with Windows' Partition Manager, but it doesn't let me to edit that partition.

Thanks for the help.

---

### Post by mikewhatever on 2009-08-24
You have to use gparted from cd. This way, the partition is not in use and you should be able to resize it.

---

### Post by raymondh on 2009-08-24
> **mikewhatever said:**
> You have to use gparted from cd. This way, the partition is not in use and you should be able to resize it.

When you do, it ought to unmount.  To ensure that partitions are unmounted, Rt. Clk on partition and if given the option to unmount, do so.  For swap, select swapoff.

---

### Post by mikewhatever on 2009-08-24
I don't think partitions are mounted in the first place when running from cd. The important thing is not to mount them before starting gparted.

---

### Post by evasquez924 on 2009-08-24
> **mikewhatever said:**
> You have to use gparted from cd. This way, the partition is not in use and you should be able to resize it.

Thanks, i'll use the GParted from CD, and then i'll tell you if it worked.

---

### Post by evasquez924 on 2009-08-25
> **evasquez924 said:**
> Thanks, i'll use the GParted from CD, and then i'll tell you if it worked.

Well, I made what you said, but I can't resize the partition to the left. I only lets me resize it to the right, but I don't want to do that.

Any idea?

---

### Post by louieb on 2009-08-25
is the partition you want to expand inside an extended partition? if so you need to expand the extended partition 1st.

---

### Post by evasquez924 on 2009-08-25
> **louieb said:**
> is the partition you want to expand inside an extended partition? if so you need to expand the extended partition 1st.

That was it! It worked perfectly.

Thanks a lot to all of you for your answers.

---

