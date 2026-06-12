---
title: "ddrescue rescued &quot;0 B&quot; under current status? I/O errors?"
date: 2012-05-18
forum: Hardware
---

### Post by XP1 on 2012-05-18
ddrescue rescued "0 B" under current status? I/O errors?

Here is a picture of the screen showing 0 bytes rescued and with /dev/sda messages on the side (are they error messages?):

[http://imgur.com/dKM9n/](http://imgur.com/dKM9n/)

There doesn't seem to be any write activity on the image drive.

The failing hard drive has been making sounds since a couple days ago. The last time that I was able to access the drive on Windows Vista was over several hours ago. I was trying to copy all files to a new drive, but the drive turned off and disappeared from Windows Explorer. After restart, Computer Management says that the drive is uninitialized. SMART status is warning about failure.

The failing hard drive (750 GB) is connected to the motherboard by SATA cable. NTFS.

The image hard drive (2 TB) is a new external USB drive. NTFS. Mounted using:
sudo mount -t ntfs /dev/sdf1 /mnt/sdf1

Using Ubuntu-Rescue-Remix 12.04.

Here is tail -f /var/log/kern.log:

[http://imgur.com/wIR3x/](http://imgur.com/wIR3x/)

What should I do?

---

### Post by ahallubuntu on 2012-05-18
If a hard drive completely fails, even ddrescue may no longer be able to access it.  You always have the option to pay someone a few hundred bucks for a clean room data recovery.

---

