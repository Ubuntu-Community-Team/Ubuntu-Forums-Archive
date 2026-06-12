---
title: "Using DD to copy a smaller drive to larger drive"
date: 2008-11-14
forum: General Help
---

### Post by mooncaptain on 2008-11-14
I have an old drive that is starting to whine like the bearings are going. I bought the smallest drive I could find on line and I need to know what is required to successfully copy the 25GB drive to the 40GB drive. 

Would a straight up dd copy work?

---

### Post by caljohnsmith on 2008-11-14
> **mooncaptain said:**
> I have an old drive that is starting to whine like the bearings are going. I bought the smallest drive I could find on line and I need to know what is required to successfully copy the 25GB drive to the 40GB drive. 

Would a straight up dd copy work?
Yes, a dd copy could work, but I'm not sure if you will be able to use the rest of the HDD space; I've read in the forums of people sometimes having problems using the remaining free space on the larger HDD. You could certainly try:
```
sudo dd if=/dev/<source drive> of=/dev/<destination drive> bs=10M conv=notrunc,noerror
```
Maybe a better option is to use the Ubuntu partition editor from your Live CD (System > Admin > Partition Editor), and you can literally copy/paste the partitions from your source drive to the destination drive. If you do it that way, you should be able to easily use the remaining space on the destination drive, including resizing the copied partitions to use that space if you want. I know a number of people who have used the "copy partition" method successfully. Anyway, let me know how it goes. :)

---

### Post by mooncaptain on 2008-11-16
I have used both methods mentioned i.e. dd and gparted and I was able to copy the partition successfully in both cases but... neither one of them would boot. That is when using the newly copied disk to boot up it would just hang in the bios.

Some new information.:

1. The source drive is actually bigger than the destination drive so I used gparted to make the partition on the source drive small enough to fit on the destination drive. I tested the source drive by booting up after shrinking the partition and it booted up fine.

2. The OS is XP not Ubuntu if that makes any difference.

3. The initial dd copy was to copy the partition /dev/sda1

I am going to use dd to copy /dev/sda less the partition reference to see if that helps.

Any other ideas are welcome.

Thanks for the ideas so far.

mc

---

### Post by caljohnsmith on 2008-11-16
> **mooncaptain said:**
> 
2. The OS is XP not Ubuntu if that makes any difference.

I think that is probably the crux of your problem; if you try and boot XP on the destination drive with the source drive connected, I don't think it will work because Windows will probably see itself as on the "D" drive instead of the "C" drive for instance. But if you replace your source drive with the destination drive that you copied XP to, you might get XP to boot. And also, if your destination drive is a USB drive, then unfortunately there's definitely no way you can boot Windows from that drive after simply cloning; even though Microsoft claims you can't boot Windows from a USB drive, some people have got it to work, but it takes *alot* of hacking.

---

### Post by mooncaptain on 2008-11-16
Hi,

These are both IDE (PATA with ribbon cables) hard drives. Source is 60GB with about 25GB partition and the destination is size is 40GB.

I tried booting up system with only the destination HD as a bootable drive and it still hangs.

I have tried copying just the source partition and the whole drive with dd. When I copy with gparted the one part of the interface says it is copying from byte 63 (more or less) not byte 0. There is another indication that it is copying from byte 0 - this is a little confusing but if it isn't copying from byte 0 there may be some missing boot information.

Any other thoughts?

---

### Post by DGortze380 on 2008-11-16
> **mooncaptain said:**
> Hi,

These are both IDE (PSATA with ribbon cables) hard drives.


Just an FYI to anyone that may have been confused about that:

IDE/PATA   (Parallel  ATA)
SATA       (Serial ATA)

There is no PSATA (Parallel Serial ATA makes no sense... it's one or the other).

---

### Post by caljohnsmith on 2008-11-16
You're right, when you copy the partition with gparted, gparted doesn't copy the MBR (Master Boot Record) of the HDD which is the first sector. But it wouldn't be a good idea to copy the entire MBR because that includes the HDD's partition table; so unless your destination drive has the exact same partitions as your source drive, it will mess things up if you copy the entire MBR of the source drive to the destination drive. You could instead just copy the boot loader portion of the MBR with:
```
sudo dd if=/dev/<source drive> of=/dev/<destination drive> bs=446 count=1
```
Then make sure the partition you copied over has the boot flag set, and that's all you should need to do as far as the MBR part is concerned.

---

### Post by mooncaptain on 2008-11-16
I am up and running with copies of my XP disk and Ubuntu disk. Thanks for all your help. In the end dd worked and gparted didn't quite do it for me although I can see how it would have been possible. I also used dd to copy a smaller Ubuntu partition to a larger drive and I do have the problem of  having two partitions on the disk. For now I am going to live with it.

---

