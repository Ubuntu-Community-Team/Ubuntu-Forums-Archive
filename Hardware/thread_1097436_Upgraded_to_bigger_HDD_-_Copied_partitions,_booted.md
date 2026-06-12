---
title: "Upgraded to bigger HDD - Copied partitions, booted ok - Free space still from old HDD"
date: 2009-03-16
forum: Hardware
---

### Post by Nefir on 2009-03-16
Ok I am not sure what's going on here...

I replaced my laptop's 200gb hard disk with a new 500gb drive. The process went easy as pie.

1) I used partimage to backup my partitions to an external disk
2) I then swapped the disk, and restored the partitions, using bigger sizes.
3) I then updated the UUID's and it boots just fine.

The old sizes for Root and Home are: 60gb and 122gb, respectively
And the new partition sizes are: 97.65gb and 373.71gb

But Ubuntu does not see the new sizes! It still thinks I'm using the old partitions.

Here is the output from df -h:

```

/dev/sda1              60G  4.7G   52G   9% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  368K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  672K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-13-generic/volatile
/dev/sda2             122G  114G  2.3G  99% /home

```

Here is fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008309b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       60227   381375067+  83  Linux
/dev/sda3           60228       60801     4610655   82  Linux swap / Solaris
```

What's going on and is there anything I can do to fix this, so that Ubuntu lets me use all that extra disk space?

I am using Kubuntu 8.10 Intrepid with KDE 4.2 on an HP HDX 18t.

---------------

EDIT:

I have resolved the problem! 

1) Boot into a rescue LiveCD with Gparted
2) Run the Gparted disk check on all partitions

Apparently it uses some tool to resize partitions that are not correctly sized - something fsck does not do on its own.

And thats all! Now my partitions are sized correctly.

---

