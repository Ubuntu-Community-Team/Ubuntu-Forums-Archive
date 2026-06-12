---
title: "[SOLVED] Swap not active on bootup."
date: 2008-09-10
forum: General Help
---

### Post by HouTxCowboy on 2008-09-10
This is my first post here, I hope I can keep this short and to the point...

Running Ubuntu 8.04LTS on my laptop, only have 512MB of ram and at the time of install I only defined 512MB of swap space (partition).  Learned about the 2x ram rule later on.  When I open several applications and browsers I quickly max out the ram and most of the swap space.  I like running several applications and utilities at the same time and using compiz-fusion for the eye candy effect.

So I booted from my live CD and re-sized my main ext3 partition from 19.5GB to 19GB using GParted.  Then I re-sized the swap partition from 512MB to 1GB.   Booted from the hard-drive and it boot fine but with no active swap partition.  So I use GParted from within the booted Ubuntu to turn on the swap space with the swapon function. That works fine until the next reboot.

I know I probably need to edit something in the /etc/fstab file but I thought I would ask for guidance before poking around in that file.  I have examined some other posting on this subject and it looks like I could of done this all from a CLI, but still would need to edit the fstab.  I also now know I could of created a additional swap file space...oh well to late now.

Any ideas or suggestions to what I need to be looking for to add or change in the /etc/fstab to get my swap partition to be active at bootup.

I can use nano or gedit to make any changes, do not want to use vi.

Thanks....
:cool:

---

### Post by sdennie on 2008-09-10
If you've changed the swap partition, the UUID has also changed.  Try the following:

```

sudo blkid

```

Find the entry that has TYPE="swap" and the long UUID string it has.  Then use:

```

gksudo gedit /etc/fstab

```

Find the entry that is swap and replace the long UUID that it lists with the one you got from the blkid command.  That should cause swap to be auto mounted at boot time.

---

### Post by dabang on 2008-09-10
I'm wondering why you need to edit /etc/fstab as you had the same swap partition before - only smaller... Only reason I could think of is that with altering the partition size the UUID also changed and because of this swap isn't acitvated automatically. If the above is the case, this should work:

```
# ls -la /dev/disk/by-uuid/
```

Copy the UUID of your swap partition. Open /etc/fstab:

```
# sudo gedit /etc/fstab
```

You should see something like this (as one line):

```
# /dev/sdaX
UUID=b28d147a-4320-49e4-be7d-04a7002a4bb3 none            swap    sw              0       0
```

Now change the UUID accordingly, reboot and you should be fine. If the correct UUID is already at it's place - well, then I was wrong...

---

### Post by dabang on 2008-09-10
OK, "vor" was faster! :lolflag:

---

### Post by grnchile on 2008-09-11
I just ran across this one as well. Your quick responses make me ashamed to admit how long it was before I noticed that my swap was gone (so I won't).

Why was /etc/fstab changed to use UUIDs? Is this for systems with multiple disks? It seems like massive (and confusing) overkill for my poor little laptop. I guess, more to the point, why aren't these generated in a way that preserves them when partitions are resized or moved, like the old /dev/sdaX names were (at least relative to their disk)? It seems like that would avoid this sort of headache.

    grnchile

---

### Post by HouTxCowboy on 2008-09-11
Thank you vor and dabang,

That fixed it...  now my LT boots with the swap area active.

This thread can be marked solved...

PS: How do you mark a thread as solved or do you just change the Title?

:cool:

PPS: Never mind....  found where to change the status to solved...

---

### Post by sdennie on 2008-09-12
> **grnchile said:**
> I just ran across this one as well. Your quick responses make me ashamed to admit how long it was before I noticed that my swap was gone (so I won't).

Why was /etc/fstab changed to use UUIDs? Is this for systems with multiple disks? It seems like massive (and confusing) overkill for my poor little laptop. I guess, more to the point, why aren't these generated in a way that preserves them when partitions are resized or moved, like the old /dev/sdaX names were (at least relative to their disk)? It seems like that would avoid this sort of headache.

    grnchile

You can still use /dev/sdaX notation in /etc/fstab if you want.  UUID is static even if you swap the order of disks (or put the disk in a different machine I think) however it can change when modifying partitions.  Using either is a tradeoff but, since the default at setup time is to use UUID, I just generally stick with that.

---

