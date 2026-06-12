---
title: "[SOLVED] hdd going bad"
date: 2008-09-26
forum: General Help
---

### Post by LashSilence83 on 2008-09-26
So I've got a hdd that is going bad on a xubuntu 8.04 machine and I have the new one to replace it with but I'd rather not have to do a fresh install if I don't have to as I've got it all tweaked and set up the way I want it. Is there some way to copy the install over or is it pretty much not worth bothering with?

---

### Post by prshah on 2008-09-26
> **LashSilence83 said:**
> So I've got a hdd that is going bad on a xubuntu 8.04 machine and I have the new one to replace it with but I'd rather not have to do a fresh install if I don't have to as I've got it all tweaked and set up the way I want it. Is there some way to copy the install over or is it pretty much not worth bothering with?

You should first try to copy the entire installation over. Here's a helpful thread: [[SOLVED] Exact duplicate of entire HDD ]("http://ubuntuforums.org/showthread.php?t=874643")

Note: If the dying hdd has any sectors marked as "bad" they will continue to be marked as "bad" on the new hdd. This will not cause any problems, except for a loss of space (possibly insignificant amount), but post back when everything is done if you want to tackle this issue as well (recheck sectors marked as bad).

---

### Post by LashSilence83 on 2008-09-27
Thanks! That worked like a charm! I was never given any errors about bad blocks, but then again I was mainly replacing the drive because it was beginning to make what I like to call the "death rattle" where it clicks incessantly every time it spins up. The only thing that was weird that I wasn't sure how to fix was that it made a partition that was the same size (6gb) as the old drive onto the new one (40gb). I tried to resize it but it sort of made it's own partitioning scheme with extra space at the end that I just ended up formatting as ext3 and decided to use as extra file storage. Is there a way to avoid that in future situations?

---

### Post by prshah on 2008-09-27
> **LashSilence83 said:**
> 
I wasn't sure how to fix was that it made a partition that was the same size (6gb) as the old drive onto the new one (40gb).  Is there a way to 
avoid that in future situations?

As discussed in the linked thread, the partition sizes will remain the same, but can be resized using gparted and a live CD, after restoration is finished.

No other solution, sorry!

---

