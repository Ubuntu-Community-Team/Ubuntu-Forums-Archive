---
title: "Primary vs logical"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by SteelCore on 2009-05-14
I normally install Ubuntu on a separate partition (dual boot with windows). During the partitioning section of the installation I always choose the primary type and it worked fine for me.  But what exactly is the difference between (primary and logical) and when do we need to use one instead of the other.

---

### Post by Partyboi2 on 2009-05-14
Hi, you can only have 4 primary partitions so to get around that you can create a extended partition and then create as many logical partitions as you need under the extended partitions.

---

### Post by SteelCore on 2009-05-14
Thanks. To reword you answer, if I want to install 4 operating systems on my harddisk I use 'primary' for each installation.  If I want 5 or more OSs then the fifth, and anything after it, will need to be an extended partion. Right?

---

### Post by coffeecat on 2009-05-14
> **SteelCore said:**
> Thanks. To reword you answer, if I want to install 4 operating systems on my harddisk I use 'primary' for each installation.  If I want 5 or more OSs then the fifth, and anything after it, will need to be an extended partion. Right?

You don't have to. You can setup logical partitions even if you have only one or two primaries. I prefer to do that because it gives me more flexibilty. A couple of things to remember: you can only have one extended partition (instead of a primary), but quite a lot of logical partitions contained within the extended. I can't remember the limit, but it's more than sufficient for my needs. The other thing is that Linux will happily boot from a logical partition, whereas Windows needs to be on a primary partition. (In fact that's not quite true - you can put the Windows C: drive on a logical, but you still need a primary for the Windows boot files.)

Also - another useful thing to know is the way that Linux numbers partitions. For the first disc (sda), sda1, sda2, sda3 and sda4 are either primaries or an extended, and sda5 and upwards are logicals.

What you could do is to put Windows on sda1 and create an extended (sda2) with however many logicals you need to install however many Linux distros you want to try out. Or, if you want to multi-boot two flavours of Windows + Linux, you could put XP (say) on sda1 and the other on sda2, then have sda3 (extended) holding your Linux partitions. **Or:** :wink:

sda1 - Windows flavour 1
sda2 - Windows flavour 2
sda3 - Shared Data partition
sda4 - extended containing your Linux partitions.

---

### Post by mikechant on 2009-05-14
> if I want to install 4 operating systems on my harddisk I use 'primary' for each installation. If I want 5 or more OSs then the fifth, and anything after it, will need to be an extended partion. Right?

Not exactly. OSs often use more than one partition. My Dell came with three partition for one install of Vista - a small FAT16 boot related partition, a Recovery partition and the main OS partition. And I needed at least two partitions - swap and root - to install Ubuntu, rising to three for the widely-recommended seperate /home partition.
So that was 6 for just two OSs!

If keeping Windows for dual boot, I'd recommend leaving the 1-3 Windows partitions as unchanged primary (apart from shrinking the main OS partition to make space), and using an extended partition for everything else.

Note that some people report that while the number of logical partitions is in theory quite large (?255), Linux may only be able to cope with 16. Others report problems with even lower numbers but this may be due to other factors.
Personally I think the most I've had was about 16 **total** partitions (3 primary and 1 extended, containing 12 logical partitions).

Note that extended partitions can be a bit of a pain in some ways - for example if you have three logical partitions sda4/5/6, and you delete and recreate sda5, it will end up as sda6 and sda6 will end up as sda5, and the partitions will be 'out of order' on the disc. This can cause confusion and possible disaster! (E.g. delete sda5, recreate it, decide you've made a mistake, delete sda5 again and you're actually deleting what was sda6 and its potentially valuable data). So always perform partition editing in cautious steps, always check the partition contents if in doubt and always back up first!

---

### Post by oldos2er on 2009-05-14
> **SteelCore said:**
> Thanks. To reword you answer, if I want to install 4 operating systems on my harddisk I use 'primary' for each installation.  If I want 5 or more OSs then the fifth, and anything after it, will need to be an extended partion. Right?

 Linux will install just fine on any extended logical partition.

---

