---
title: "Not all space is available on /home"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by spinstartshere on 2009-06-01
I resized my home partition when I reinstalled Ubuntu but I am only able to use as much space as I had before.  How can I gain access to the whole partition?

---

### Post by logos34 on 2009-06-01
post the output of these commands:

sudo fdisk -l

df -h

and maybe throw in a screenshot of Gparted 

sudo gparted

---

### Post by spinstartshere on 2009-06-01
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb58e199

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275        6095    38724682+   7  HPFS/NTFS
/dev/sda3            6096       19033   103924485    f  W95 Ext'd (LBA)
/dev/sda4           19395       19457      506047+   7  HPFS/NTFS
/dev/sda5            6096        8706    20972794+  83  Linux
/dev/sda6            8707       18369    77612032   83  Linux
/dev/sda7           18387       18770     3084448+   7  HPFS/NTFS
/dev/sda8           18771       19033     2112516   82  Linux swap / Solaris

---

### Post by logos34 on 2009-06-01
you forgot 

df -h

How much extra space did you expect to gain?  Because it's showing a bit of unallocated space between sda6 and sda7, but it's only 139 mb.  Also, there is ~2.7 gb after/outside the extended partition...To give it /home you'd have to grow sda3 to incorporate it, then use the gparted 'move' function to move sda7 and swap to the end, then expand /home.

---

### Post by spinstartshere on 2009-06-01
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G  3.5G   16G  19% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  216K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  176K 1003M   1% /dev
tmpfs                1003M  396K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-12-generic/volatile
/dev/sda6              50G   46G  3.8G  93% /home
```I was expecting to gain a few gigabytes.  As you can see, I only have 50 GB available on that partition, which is the size it was before.

---

### Post by logos34 on 2009-06-01
ok, so do like I said above and that will allow you to add the space that is now outside the extended partition to the /home inside

---

### Post by spinstartshere on 2009-06-01
I don't want the space outside the partition, I want the space that is assigned to it.  The partition is 74.02 GB in size but I'm only able to access 49.2 GB.  As a result, 45/74.02 apparently equals 0.92.

---

### Post by drs305 on 2009-06-01
Did you copy an image to restore your /home partition. If so, to get ubuntu to recognize the full partition size, you can run e2fsck and then resize2fs to reset the correct partition size. Since this has to be done while /home is unmounted you will have to do this from the LiveCD.

```

sudo umount /dev/sda6
sudo e2fsck -f /dev/sda6  # check for errors
sudo resize2fs /dev/sda6  # resize
df -h

```

---

### Post by spinstartshere on 2009-06-01
I didn't use an image, I just resized the partition while using the LiveCD before installing the OS.  Should I still do this and can I do it in recovery mode?

---

### Post by drs305 on 2009-06-01
> **spinstartshere said:**
> I didn't use an image, I just resized the partition while using the LiveCD before installing the OS.  Should I still do this and can I do it in recovery mode?

This situation is often the result of restoring a smaller image to a larger partition, but the commands may still 'reset' things to accurately reflect what is going on.

If this does not correct the problem, the next method would involve using TestDisk. There are numerous posts about how to install and use it.

For either method, the /home partition must be unmounted which will require the LiveCD or something such as the SystemRescueCD.

---

### Post by spinstartshere on 2009-06-01
It worked, thank you.

---

### Post by logos34 on 2009-06-01
ok, I somehow missed the '50 gb' on the df -h readout...I would have suggested testdisk because sometimes gparted doesn't get the partition table right...but maybe fsck and resize2fs as drs305 suggested will correct it

---

### Post by VastOne on 2009-06-01
> **drs305 said:**
> Did you copy an image to restore your /home partition. If so, to get ubuntu to recognize the full partition size, you can run e2fsck and then resize2fs to reset the correct partition size. Since this has to be done while /home is unmounted you will have to do this from the LiveCD.

```

sudo umount /dev/sda6
sudo e2fsck -f /dev/sda6  # check for errors
sudo resize2fs /dev/sda6  # resize
df -h

```

drs305

Thanks for this code...I just went through a dd image process and was wondering about just this and here you are deftly splainin it:cool:

---

