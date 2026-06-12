---
title: "Can't mount hard drive"
date: 2016-12-05
forum: Hardware
---

### Post by Maheriano on 2016-12-05
I had trouble mounting this drive years ago and somehow did get it working, now I'd like to finally get the data off of it before retiring it permanently. I'm having trouble mounting it once again, I'm pretty sure I've corrupted something in the partition table somehow. Here is what I have:

1. When trying to mount it normally by clicking the drive icon on the desktop nothing happens.

2. When trying to mount it via the Disks utility, I get an error:

> Error mounting filesystem
Error mounting /dev/sda1 at /media/deemar/Hyperspin: Command-line mount-t "ntfs" -o "uhelpter=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/deemar/Hyperspin" exited with non-zero exit status 12: NTFS signature is missing.
Failed to mount "/dev/sda1": invalid argument
The device /dev/sda1" doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition? (e.g. /dev/sda, not /dev/sda1)? Or the other way around? (udisks-error-quark, 0)

3. ```
deemar@Mulder:/media$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           786M   10M  776M   2% /run
/dev/sdb2       909G  358G  505G  42% /
tmpfs           3.9G  457M  3.4G  12% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       511M  3.6M  508M   1% /boot/efi
tmpfs           786M   92K  786M   1% /run/user/1000

```

4. ```
deemar@Mulder:/media$ sudo mount -t ntfs /dev/sda1 /media/hyperspin/
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

5. ```
deemar@Mulder:/media$ sudo mount -t vfat /dev/sda1 /media/hyperspin/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

What are my options here?

---

### Post by DuckHook on 2016-12-05
Have to read between the lines a lot to decipher your setup but I gather that the HDD is NTFS, probably an old Windows-formatted disk, and that you are trying to retrieve Windows-created files? If so, then I would suggest that you use Windows tools (running in Windows, obviously) to try salvaging your HDD. Rule of thumb is: Windows tools for Windows disks; Linux tools for Linux disks.

As a side note, the error messages are saying that you have a bad file table/structure/super block. However (and it's a big however), these are Linux tools reporting on what is ultimately an alien filesystem. It is unwise to rely on such reports any more than you would rely on an engineer reporting your medical results.

---

