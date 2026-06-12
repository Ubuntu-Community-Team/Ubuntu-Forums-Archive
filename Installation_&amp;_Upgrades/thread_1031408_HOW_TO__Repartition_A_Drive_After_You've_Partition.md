---
title: "HOW TO:  Repartition A Drive After You've Partitioned It"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by N00bB00b on 2009-01-05
So, you partitioned your drive, and you've installed Ubuntu.  When you did that you decided to leave part of your drive empty so you could allocate it later.  Now you want to use that empty space, but you don't seem to be able to do it.  Now what?

This is really easy, but it took me a couple of hours of reading and playing to figure it out.

1. **Boot from a livecd.**  You are doing this because it will leave the filesystem on your hard drive unmounted, which is important.
2. **Administration->Partition Editor.**
3. **You'll see that your logical partition is probably locked (either with a lock icon or keyring icon).**  You'll also probably notice that swap is locked.
4. **Right-click on swap and choose "swapoff".**
5. **Delete swap.**
6. **Right-click on the top line for the extended partition you are editing **(you put all of your ubuntu partitions into one extended partition, right?)
7. **Resize the extended partition to the size you need to include the new partitions you are going to create.** (Right-click, resize).
8. **Create the new partitions.**
9. **Re-create swap.**
10. **Right-click on swap and pick "swapon".**
11. **Reboot.**
12. **Put a thank-you on this thread.**

---

