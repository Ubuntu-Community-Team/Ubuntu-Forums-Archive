---
title: "RAID 1 configuration (non-boot)"
date: 2008-11-14
forum: General Help
---

### Post by bgiddins on 2008-11-14
Can anyone point me at a concise guide for creating a RAID 1 mirror on Ubuntu 8.10? This is for a non-boot volume - I have my OS on a separate drive, so this is just for data.

I've read so many conflicting setup steps on this forum and others I'm at a loss. So far I've done the following to two 1TB drives that both had a single partition that I removed all data from:

$ sudo fdisk /dev/sdb
(deleted the existing partition sdb1)
(created a new RAID partition with n > p > 1 > ENTER ENTER > t > fd > w)

I repeated the above on sdc (it had a partition sdc1).

I then created the array with:

$ sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb /dev/sdc

This ran overnight. After completing, I ran the following command and got the following output:

$ sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=a3dfaad9:d06b640d:9652887a:14159a7a

Now - I'm at a loss as what to do from here - rebooting fails because GRUB can't find the old partitions, and I need to hit Control-D to finish booting.

Trying to mount the mirror gives the following:

$ sudo mount /dev/md0
mount: can't find /dev/md0 in /etc/fstab or /etc/mtab

I've looked in fstab, and it still has references to the old sdb1 and sdc1.

I'm at a point where I need to do *something* in the following, but am not sure which - can someone give me some pointers?

/etc/fstab
/etc/mtab
/etc/mdadm/mdadm.conf

I'm running 8.10 Server 64-bit edition with ubuntu-desktop installed. I'm worried I executed mdadm incorrectly, RAIDing drives instead of partitions if that makes sense.

---

### Post by bgiddins on 2008-11-15
Found my mistake - I used mdadm against the drives, not the partitions on the drives!

$ sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1

Now I need to figure out how to get /dev/md0 to mount with a new name - it picked up the partition mount point from sdb1 (which was /sata2 when it was a standalone disk). I can't figure out how to rename /dev/md0 so it mounts to, say, /mirror.

---

### Post by fjgaude on 2008-11-15
Why not create a mountpoint for your array, like so:

```
sudo mkdir /home/raid
```

Then in your /**etc/fstab** file put this line:

```
/dev/md0 /home/raid ext3 defaults 0 2
```

Of course you can call the mountpoint anything you wish; it can even be off /, like /raid.

Let us know how things are going.

Say, you did put a filesystem in the array after you created it, eh?

BTW, to mount an array or drive you have to state a mountpoint:

```
sudo mount /dev/md0 /home/raid
```

As an example.

---

### Post by bgiddins on 2008-11-22
I thought I would start from scratch - so I fired up a Live CD and used gparted to reformat the two drives, and attempt to create the array "cleanly". RAID 1 had been working - I am using gkrellm as a system monitor, and could see read/write activity to both drives in the array.

Now I've gone and broken it again :)

I rebuilt the array using the same steps that ended up working for me the first time:

```
$ sudo fdisk /dev/sdb
(deleted the existing partition sdb1)
(created a new RAID partition with n > p > 1 > ENTER ENTER > t > fd > w)
```

Repeated for /dev/sdc

```
$ sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1
```

This took a couple of hours (1TB drives!) - then I was able to mount the array like you suggested:

```
$ sudo mkdir /mirror
$ sudo mount /dev/md0 /home/raid
```

I also added the line to /etc/fstab.

Now - I get an error on boot, and the array does not auto-mount - when I did it previously, it just auto-mounted on reboot and was all good - now I have to hit Control-D on every boot, and go in and repeat the manual mount for the array to be available. It does work though when mounted.

Ideas on why this time it doesn't auto-mount? The glaring difference to me is that I built the array from two brand new partitions, rather than reusing ones that were set to mount to /sata2 and /sata3 when I first installed the OS.

---

### Post by bgiddins on 2008-11-22
Okay, just found this bookmarked from last time :)

[http://www.mepis.org/docs/en/index.php/Software_RAID_mirror](http://www.mepis.org/docs/en/index.php/Software_RAID_mirror)

I had to run:

```
$ e2fsck /dev/md0
$ resize2fs /dev/md0
```

Problem solved - and I now have a RAID 1 array auto-mounting at /mirror, which is what I wanted originally.

Thanks!

---

### Post by fjgaude on 2008-11-22
What are you going to do when one of the drives fail and you have to replace it? Just a thought, eh?

---

### Post by bgiddins on 2008-11-23
> **fjgaude said:**
> What are you going to do when one of the drives fail and you have to replace it? Just a thought, eh?

Buy another 1TB disk and learn how to repair a mirror :)

The data on the array is backups from other machines, and snapshots of VMs from a separate drive within the same machine. IF I lost all the data on the array, it's a matter of having lost online backups rather than the only copy of data. All the "good" stuff like photo collections etc also have DVD backups in a safe deposit box :)

As such, I don't *need* RAID 1, but this is a home machine, and I'm using it to expand my hands-on knowledge. I work primarily in software, so I don't mind learning this stuff to give me a better understanding of storage considerations (even though most of the work related stuff I work with is sitting on a SAN somewhere). I expect that some time next year I'll be adding disks and trying out RAID 5 or 10 depending on how much internal space I decide I want. There's a few things I want to try, like setting up RAID 5 on 3 disks plus a hot spare, and then simulating a disk failure and online rebuild, as well as setting up RAID 10. All a learning exercise.

---

### Post by fjgaude on 2008-11-23
Thanks, and that sounds good to me... maybe you could write a HOW-TO after you learn all these things... mdadm certainly could use a good book that covers all the situations one runs across as drives fail, expansion of array size is needed, etc.

---

### Post by Virtual_Ron on 2009-09-27
Hi,

I've set up a raid1 (non-os).   I followed bgiddins' examples exactly to the letter.  hell, even my device names are identical.

Everything works great...until I restart my system.

When booting, I get:  
fsck.ext3: No such file or directory while trying to open /dev/md0

I have to "control-D" to continue boot.

When I run "cat /proc/mdstat" is get:
[B]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdc1[1](S)   
[/B]
I type:
mdadm --stop /dev/md_d0  
mdadm -A --scan
and it fires the array up no problem.
I can run mount -a, and I'm back in business.

When setting up the raid, I've followed the instructions and ran:
e2fsck /dev/md0
resize2fs /dev/md0

I've run  "dpkg-reconfigure mdadm"

But, everytime I reboot... md0 is gone.

Anyone have any tips on getting my raid to start upon boot?

many thanks!

---

### Post by Virtual_Ron on 2009-09-27
well, I figured it out.

Seems there's a known Jaunty Jackalope bug that breaks mdadm.
the mdadm.conf gets broken.

Just need to run:  mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

and you're good to go.

---

