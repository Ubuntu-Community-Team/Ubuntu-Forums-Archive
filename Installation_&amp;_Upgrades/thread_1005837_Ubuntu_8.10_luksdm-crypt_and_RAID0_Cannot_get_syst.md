---
title: "Ubuntu 8.10 luks/dm-crypt and RAID0 Cannot get system to run!"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by RansomStark on 2008-12-08
So,

I am using the Ubunutu 8.10 i386 alternate boot CD.
I have pre-wiped 2 SATA 80GB drives.
Run the install and choose manual for the drive partition.

I create 3 RAID array's across the 2disks (sda & sdb)

RAID1 /boot 200mb
RAID0 swap 500mb
RAID0 / 75GB

Now, after generating the RAID devices (md0, md1 & md2) I now choose to create an encrypted partition on md1 (swap raid0) and md2 (/ raid0) I leave the /boot partition on RAID1 with no encryption.

I only tick the bootable flag to the /boot volume on sda.

Then once this completes I create the / as ext3 and swap as swap. All seems good!

Install completes, and usually a combination of things happen. Either grub cannot find the filesystem. Or grub boots but the encryption key I entered does not work (I am purposely using something easy as this is just to test the setup).

Is what I am trying to do possible?
Can anyone give me any pointers as to what I may be doing wrong

Thanks in advance!

---

### Post by RansomStark on 2009-01-02
In case anyone else is reading my post and having the same problem, the answer was quite annoying. Basically there is a bug in the 8.10 installer, so trying to manually setup the disk with encryption and raid resulted in a behind the scenes change to the partition table so that a LVM was created, which then failed to operate correctly because the partitions created did not match what I had setup in the crypttab.

If you drop down to 7.10 or 8.04 then this setup works (almost), except don't create the /boot on a RAID partition as its more trouble than its worth to boot (baring in mind I was going for RAID1 on my partitions so not interested in redundancy so having /boot on sda1 is OK). The only catch is the random key option for your swap partition doesn't work! So create the partition but set to do not use then manully once up and running create the swap partition as follows:

My drive was /dev/md1

```
sudo cryptsetup create swap /dev/md1
```
add this line to your /etc/crypttab

swap        /dev/md1    /dev/urandom swap

```
swapon -a
```
```
sudo swapon /dev/mapper/swap
``` 

Then a reboot was required to ensure it all worked properly.

---

