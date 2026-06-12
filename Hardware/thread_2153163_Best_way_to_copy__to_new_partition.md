---
title: "Best way to copy / to new partition"
date: 2013-06-10
forum: Hardware
---

### Post by RecceDG on 2013-06-10
Over the weekend, I added a pair of 3TB drives to my 12.04 LTS box, as a RAID 1 array.

This was to replace / expand the /home directory on my root RAID 1 filesystem. The install went perfectly, no problems at all.

I did, however, make one of those "Was I on crack when I did this?" discoveries:

The existing pair of drives was partitioned as /boot, /, swap, and /home. Both drives identical. /home was mounted as a RAID 1 array, and I *thought* / had been as well, but it turned out that it was not - the partition was in place (and had a filesystem on it, and mounted) but it was empty.

Whoops.

I had also learned that the /boot partition was a little small, and I wanted to add a little more swap, so I failed & stopped the drive (to take it out of the RAID array serving /home) and then re-partitioned it - same partition names and sequence, but resized to better fit the requirements of the system.

I then created a pair of new RAID 1 arrays, one for / and one for /oldhome, but with the second disk of each array missing. The idea being to copy the contents of / and /home over onto the RAID arrays, boot off the drive with the RAIDs on it, repartition the previous boot drive to match the new partition scheme, and then add the RAID partitions into the already-created arrays and let the drives sync themselves up.

So far, so good. Everything works as expected.

I'm at the point now where I have to copy the existing / partition contents onto the new / RAID partition. I had used the find | cpio trick to copy the /home filesystem to its new home (find / -xdev -print0 | sudo cpio -pa0V /newroot) but that doesn't appear to have properly worked - for example, there are simlinks to the /boot partition (for vmlinuz and initrd.img) that didn't get copied... and my confidence level that the various special files for /dev, /sys etc are properly accounted for and otherwise have been handled properly is not high.

So what's the best way to copy the / filesystem to the new partition, with the end state that I can immediately boot off the target drive (post an /etc/fstab edit) and have everything just work?

Thanks,

DG

---

### Post by RecceDG on 2013-06-11
Huh, I thought this would have generated some traffic by now:

OK, possible solutions:

1. Some variation of a copy process (cp, tar, cpio etc) to copy from / (the live root filesystem) to /newroot (the RAID 1 array that will become the new root); or

2. Boot into a LiveCD, mount the / and /newroot filesystems, and do some form of copy (tar, cpio etc) to do the copy, but as the special files like /proc won't be mounted on the / partition on the old drive, there's no Weird Harolds to deal with; or

3. Boot from an install CD, mount only the filesystems on the new drive, and then do a fresh install onto it. Then do something that compares the old package database to the new package database, and install the delta. Then copy over the old /etc and hope for the best.

I'd prefer a solution that doesn't require a CD though... any ideas?

---

### Post by ahallubuntu on 2013-06-11
~

---

