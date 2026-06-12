---
title: "Unknown Free Space"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by MadeOfEyelashes on 2009-06-17
I'm trying to install Ubuntu 9.04. I have a 320 Gig harddrive built into my laptop. I want to have two partitions, one with Windows 7 RC (x64) and one with Ubuntu 9.04. I had it working before, but deleted Ubuntu because I wasn't using it often. Now I want to put it back on because I miss it :(

However, when I am going to install Ubuntu, I get to Step 4 and it says I have no free space. Windows says I have 51% free space. I checked under advanced and Ubuntu says "unknown free space"

How can I fix this?

---

### Post by merlinus on 2009-06-17
Did you use win7 disk manager to shrink its partition?  If not, defrag first, and then shrink.

Also, you can use gparted on the live cd to format the ubuntu partition as ext3 before installing.

---

### Post by Mark Phelps on 2009-06-20
If the "free space" is inside your Windows 7 partition, you won't be able to use it because Wubi (installing inside Windows) has lots of problems with Windows 7.

You would do better using Disk Management to shrink the Windows 7 partition, and then install Ubuntu in a dual-boot scenario, in its own partitions.

---

