---
title: "Weekend Partitioning Project and Problem..."
date: 2009-09-13
forum: Hardware
---

### Post by andrewbrown22 on 2009-09-13
I recently had a desktop PC completely fail out on me. I can't do anything with it, but I can access the drive. It was of course the one that I used for my iPod and iPhone syncing.  Great.

I've decided that I should have been using my newer and faster laptop all this time for those purposes anyway, and it's already set up with a dual boot of Win XP and Ubuntu 9.04.  However, my XP partition is not nearly big enough for my music collection: I need to resize the partitions. 

I started this project early yesterday. I resized the ~250GB Ubuntu partition down to 200GB. Leaving the extra space to the left of the partition. I can't however figure out how to expand the ntfs area to include this newly freed up space.

What am I doing wrong? I'll post a screenshot of the current Gparted program.

And yes, I am doing this from a LiveCD, not from within the drive I'm trying to resize.

---

### Post by Vaphell on 2009-09-13
i see a potential problem in the fact that your ntfs is a primary partition and freed space is in inside the extended partition - i suspect you'd have to resize down extended first.

---

### Post by andrewbrown22 on 2009-09-13
Ok, and how would I do that exactly?

---

### Post by andrewbrown22 on 2009-09-13
I'm just not quite sure how to do that or what it is that I need to do in order to get this ntfs partition expanded to the unallocated space. Can anyone explain it to me?

---

### Post by arrange on 2009-09-14
Mark the *swap* first and go to Partition &#8594; Swapoff. Then mark */dev/sda2* (extended partition) and you should be able to resize it to the right (reduce the size). Then expand *sda1* to the new space.

---

### Post by andrewbrown22 on 2009-09-14
> **arrange said:**
> Mark the *swap* first and go to Partition &#8594; Swapoff. Then mark */dev/sda2* (extended partition) and you should be able to resize it to the right (reduce the size). Then expand *sda1* to the new space.

That's exactly what I did yesterday after messing around with it for a while. Thanks for the help, this is exactly all that needed to be done, just wish I'd been told earlier. Still, problem solved.

---

