---
title: "Connect external hard disk"
date: 2009-09-20
forum: Hardware
---

### Post by hudsongates on 2009-09-20
Hi there,

I am working on a server which is used to host a handful of virtual machines.  The host OS is Ubuntu 6.  I need to get the VMs off the main disk (the internal HDD), and on to an external 500 GB drive (which happens to be freshly formatted NTFS).

When I execute df, I get the following result:

```

Filesystem             1K-blocks       Used  Available Use%  Mounted on
/dev/sda1               28929052     238788   27220720   1%  /
varrum                   4157012        108    4156904   1%  /var/run
varlock                  4157012          4    4157008   1%  /var/lock
udev                     4157012         92    4156920   1%  /dev
devshm                   4157012          0    4157012   0%  /dev/shm
/dev/mapper/vg01-home  353848364  224879028  110994860  67%  /home
/dev/mapper/vg01-usr    41284928    1598288   37589488   5%  /usr
/dev/mapper/vg01-var    41284928     436580   38751196   2%  /var

```

When I plug the USB HDD in to the server, after about 10 seconds I get the following message on screen:

```
[42949966.320000] sdc: assuming drive cache: write through
```

When the above message appears, it just sits there doing nothing - I have left it for about 10 minutes to see if it was just taking a long time to do whatever it is doing, but I don't think it is actually doing anything.  When I press "Enter", the screen returns to the command prompt.

After connecting the USB disk, when I execute df the results are the same.  

Q1.  What does the above message mean?  Is it an error?
Q2.  How do I get the external drive to be recognised by Ubuntu?
Q3.  Does it matter if the external drive is NTFS?

Cheers,

Paul Hobbs

---

### Post by bogdan.veringioiu on 2009-09-20
Hi.

What does "sudo fdisk -l" give, after you plug in the usb disk?
Cheers.
Bogdan

---

### Post by hudsongates on 2009-09-21
I tried restarting the server (with the USB disk plugged in), and when I execute "sudo fdisk -l", I get the following output:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start          End    etc    System
/dev/sda1   *         1         3659           Linux
/dev/sda2          3660         5604           Linux swap / Solaris
/dev/sda3          5605        30401           Linux LVM

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start          End    etc    System
/dev/sdb1             1        30401           Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start          End    etc    System
/dev/sdc1   *         1        60801           HPFS/NTFS
```

Obviously /dev/sdc is the external drive, which I guess means that it is being correctly detected by Ubuntu, so presumably now I just need to mount it.

---

### Post by bogdan.veringioiu on 2009-09-21
Yes.

Just try:
sudo mkdir /media/myntfsdrive
sudo mount /dev/sdc1 /media/myntfsdrive

Cheers

---

### Post by hudsongates on 2009-09-21
That worked, but it seems that the drive is read-only.  I have tried using chmod to change the permissions, but it doesn't seem to want to change - I keep getting the message that it is a read-only file system.  I guess that is because it is NTFS.  I assume I can reformat the drive as ext3 (or some other Linux-friendly file system).

I haven't done this before, but am I correct in thinking that I need to use the mkfs program?

---

### Post by bogdan.veringioiu on 2009-09-21
If you will use the drive in the linux world, yes, it is better ext3 filesystem.

If you want to do this, then I think the correct way is:
-umount volume (sudo umount /media/myntfsdisk)
-sudo fdisk /dev/sdc
-delete ntfs partition
-create ext3 partition
-exit fdisk
-run sudo mkfs.ext3 /dev/sdc1

Bogdan

---

### Post by hudsongates on 2009-09-21
New file system is mounted and working nicely - thx for your help.

---

### Post by bogdan.veringioiu on 2009-09-21
Ok.
Glad to see it works.
Bye
Bogdan

---

