---
title: "How do I change default drives?"
date: 2013-05-08
forum: Hardware
---

### Post by braedentraut24 on 2013-05-08
I have my 305 GB Filesystem mounted but while installing MinecraftServer.exe, my laptop said I didn't have enough room on my disk.  I then went to disk usage analyser and looked at how much space I had.  I had about 299 Gigs remaining.  I already have the drive mounted and I have gParted but I can't partition my /dev/sda7 to a bigger size.  I also don't even know if my hard drive is really being used at all.  I have tons of space left but it just[SIZE=5] wont work![SIZE=2]I'm not really sure what to do at this point because 10 GB is not enough for me to really do what I want at all!  

 Thanks
-Braeden[/SIZE][/SIZE]

---

### Post by ibjsb4 on 2013-05-08
Did you unmount the partition before you tried to resize it?

[http://www.dedoimedo.com/computers/gparted.html#mozTocId661277](http://www.dedoimedo.com/computers/gparted.html#mozTocId661277)

---

### Post by papibe on 2013-05-08
Hi braedentraut24.

Could you open a terminal, run these commands and post its results?
```
df -h

df -i

sudo fdisk -l

mount -l
```
Regards.

---

### Post by braedentraut24 on 2013-05-08
> **papibe said:**
> Hi braedentraut24.

Could you open a terminal, run these commands and post its results?
```
df -h

df -i

sudo fdisk -l

mount -l
```
Regards.
Yes I could

---

### Post by braedentraut24 on 2013-05-08
This is what I got (the screen was too big too take a screen shot of so i just copy/pasted it)
```
user@ChrUbuntu:~$ df -h
Filesystem                                                                 Size  Used Avail Use% Mounted on
/dev/sda7                                                                   10G  8.5G  1.1G  89% /
devtmpfs                                                                   2.9G  4.0K  2.9G   1% /dev
none                                                                       590M  724K  590M   1% /run
none                                                                       5.0M     0  5.0M   0% /run/lock
none                                                                       2.9G  332K  2.9G   1% /run/shm
/dev/sda8                                                                   16M  1.3M   14M   9% /media/OEM
/dev/mapper/udisks-luks-uuid-85298ea9-817d-4429-a878-442513e8eecc-uid1000  284G   32K  284G   1% /media/Hard Drive
```
```
user@ChrUbuntu:~$ df -i
Filesystem                                                                Inodes  IUsed  IFree IUse% Mounted on
/dev/sda7                                                                 655360 241656 413704   37% /
devtmpfs                                                                  754716    476 754240    1% /dev
none                                                                      755033    489 754544    1% /run
none                                                                      755033      3 755030    1% /run/lock
none                                                                      755033      8 755025    1% /run/shm
/dev/sda8                                                                   4096     11   4085    1% /media/OEM
/dev/mapper/udisks-luks-uuid-85298ea9-817d-4429-a878-442513e8eecc-uid1000      0      0      0     - /media/Hard Drive
```
```
user@ChrUbuntu:~$ sudo fdisk -l
[sudo] password for user: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/mapper/udisks-luks-uuid-85298ea9-817d-4429-a878-442513e8eecc-uid1000: 304.9 GB, 304858791936 bytes
255 heads, 63 sectors/track, 37063 cylinders, total 595427328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


                                                                     Device Boot      Start         End      Blocks   Id  System
```
```
user@ChrUbuntu:~$ mount -l
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
devtmpfs on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sda8 on /media/OEM type ext4 (rw,nosuid,nodev,uhelper=udisks) [OEM]
/dev/mapper/udisks-luks-uuid-85298ea9-817d-4429-a878-442513e8eecc-uid1000 on /media/Hard Drive type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks) [Hard Drive]
user@ChrUbuntu:~$
```

---

### Post by papibe on 2013-05-08
Thanks.

Your root partition (/dev/sda7) is only 10Gb, and it has only around 1Gb of free space.

Unfortunately, you can't resize it while is being used. You have to use a Live media to solve your problem. If you still have the Ubuntu installation CD/USB around somewhere, that will work. Boot into the installation media, and select 'Try Ubuntu' instead of initiating the installation process.

Once you get to the desktop, you can run gparted (pre installed) to resize the partitions of the internal disk. Note that the names may be different, e.g., sdb instead of sda, but you'll recognize the correct disk because of its size.

Hope it helps. Let us know how it goes.
Regards.

---

