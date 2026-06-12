---
title: "NVRAID on Ubuntu 10.10"
date: 2011-01-31
forum: Hardware
---

### Post by daveisfera on 2011-01-31
I just installed Ubuntu 10.10 on a computer and now I'm trying to setup a RAID on my MSI MSI K9N2GM-FIH as a "data drive". I have the RAID mode set to RAID in the BIOS and the device shows up as /dev/dm-0 (which is also linked to at /dev/mapper/nvidia_egceceeh).

I opened up /dev/mapper/nvidia_egceceeh in fdisk and created a partition, but after a restart when I ran mkfs.ext4, I got the error:
/dev/mapper/nvidia_egceceeh is apparently in use by the system; will not make a filesystem here!

mount doesn't show anything related to that and a umount says it's not mounted, so is there something I'm missing?

I did find this wiki: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
But it is geared towards installing onto the hard drive (which I don't want to do) and doesn't have any info about 10.10, so is there another reference I can look at or some other info I can check out as far as getting this setup?

Thanks,
Dave

---

### Post by ronparent on 2011-02-01
I would suggest your using gparted, the graphic interface partitioner, to create partitions on the raid. If for some reason the raid doesn't show up in gparted then install kpartx to enable it. If the 'in use' message appears you might try logging out and back in to try to clear it. Good luck.

---

### Post by Pernig on 2011-02-01
I would recommend using gparted to set up the partitions on your new drive and then putting entries for them into /etc/fstab so you can set the mount points, owner etc.

If you can only get sda, sdb, sdc etc on Gparted, then try this:

```
$ sudo gparted /dev/mapper/nvidia_egceceeh
```

On an unrelated note, make sure you back up regularly when using the Nvidia firmware RAID. It can be a real pain to fix when things go wrong!

---

### Post by psusi on 2011-02-01
You want to format the partition, not the whole raid array.  In other words, you left off the partition number.

---

### Post by ronparent on 2011-02-02
With gparted it is valid to call up the entire array, especially if there are no partitions yet formatted.

---

### Post by psusi on 2011-02-02
> **ronparent said:**
> With gparted it is valid to call up the entire array, especially if there are no partitions yet formatted.

Yes, because that is a partitioning tool, mkfs is not.

---

### Post by ronparent on 2011-02-02
Your right!

---

