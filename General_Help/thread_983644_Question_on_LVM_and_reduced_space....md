---
title: "Question on LVM and reduced space..."
date: 2008-11-15
forum: General Help
---

### Post by Th3Professor on 2008-11-15
Three of my hard drives (each 500GB) have been set up with RAID5.
I'm aware that of the 1.5TB I will have a working 931GB via that RAID.
After setting up RAID5, I followed with setting up an LVM.
After setting up LVM, I discovered a drop in capacity and space available.

I am curious, why is the capacity now 14GB less?

Likewise, why also is 200MB being used (although I see it nowhere)?

I expected to see the following when checking *df* on the lvm-raid:
931GB size, 0 used, 931GB available (or very close, at least).

Instead, this is what *df* reads for the lvm-raid:
917GB size, 200MB used, 871GB available.

I am a bit puzzled at this. I understand that I must sacrifice some space when setting up a RAID (though technically it's no sacrifice for the benefit it provides). However, I had no idea that LVM might either reduce the capacity even more *or* use space out of the capacity. 

Could this mysteriously reduced capacity and mysteriously used space be the result of creating a file system within RAID and again within LVM?

More specifically: If someone creates an ext3 (4096-byte block size, 32 blocks (stride-size))  for their 128 chunk-size RAID set-up and follows that with creating an ext3 (same block/stride/etc.) for their parallel-sized LVM set-up, could the twice-over file system creation be the reason for that drop in capacity and increase in space used?

Or could it be the result of using 32MB physical extent size on the volume via vgcreate?

Both? Or something totally different?

Going from 1.5TB to 931GB (for RAID) is obviously a much larger drop than 931GB to 917GB (for LVM), though I'm curious as to why there was even a drop in capacity after setting up LVM+RAID. I didn't know that LVM also costs space to create (unless I simply did something incorrectly in the set-up).

Thanks!  :-)

---

### Post by boblemur on 2008-11-16
i dont think that this is LVM related, the used space is from ext3, when u format a clean disk with 1 partition this ammount of space comes up as used also :S i dono what its from... but its always there...


the other thing the loseing total space on ur LVM i dont know about that... but it may simply be a rounding/represenation thing. who knows sorry i cant help with the main part of ur qn

---

### Post by Th3Professor on 2008-11-16
> **boblemur said:**
> i dont think that this is LVM related, the used space is from ext3, when u format a clean disk with 1 partition this ammount of space comes up as used also :S i dono what its from... but its always there...


the other thing the loseing total space on ur LVM i dont know about that... but it may simply be a rounding/represenation thing. who knows sorry i cant help with the main part of ur qn

That helps a little though, still, I appreciate it... that is odd that ext3 takes up space, I didn't know it'd do that. How much space does it usually take up?

Maybe it's the combination of raid+ext3+lvm+ext3?

Maybe I should do it with just raid+lvm+ext3... not sure.

---

