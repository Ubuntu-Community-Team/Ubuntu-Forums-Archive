---
title: "External USB Drive not mounting under superuser"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by mtxcoll on 2007-11-15
When I first started using Ubuntu my external harddrive (Seagate, 160GB) mounted but required using sudo from the console. However, for some reason now my hard drive isn't even being sensed by Nautilus and trying to mount via superuser doesn't work.
```

$ mount /media/seagate
fusermount: user has no write access to mountpoint /media/seagate
FUSE mount point creation failed
$ sudo mount /media/seagate
Error opening partition device: Permission denied
Failed to mount '/dev/sdb1': Permission denied

```

cat /etc/fstab
```

# Entry for /dev/sda1 :
UUID=6e62d2d8-e9f5-496d-99c2-bd23c7976646 /home ext3 nodev,nosuid 0 2
# Entry for /dev/sda2 :
UUID=82e89a31-e002-44ce-aa31-0c6a3225fa9a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=4719803a-b2ee-4884-b996-dd578e8b3878 none swap sw 0 0
# Entry for /dev/sdb1 :
UUID=F470A65F70A62876 /media/seagate ntfs user,rw,iocharset=utf8,defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

cat /etc/mtab
```

/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /home ext3 rw,nosuid,nodev 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0

```

fdisk -l
```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a57c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19455   156272256    7  HPFS/NTFS

```

cat /etc/fuse.conf
```

# Set the maximum number of FUSE mounts allowed to non-root users.
# The default is 1000.
#
#mount_max = 1000

# Allow non-root users to specify the 'allow_other' or 'allow_root'
# mount options.
#
#user_allow_other

```

ls -l /media/
```

lrwxrwxrwx 1 root root    6 2007-10-20 15:36 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-10-20 15:36 cdrom0
drwxr-xr-x 2 root root 4096 2007-11-15 09:19 isoimage
drwxr-xr-x 2 root root 4096 2007-11-15 15:18 seagate

```

I was messing with some of the file permissions trying to allow mounting without having to open up a console or run a script that uses sudo, and I must have screwed something up. Any help is appreciated!

---

### Post by taurus on 2007-11-15
What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sdb1 /media/seagate
```

---

### Post by mtxcoll on 2007-11-15
> **taurus said:**
> What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sdb1 /media/seagate
```
```

$ sudo mount -t ntfs /dev/sdb1 /media/seagate
Error opening partition device: Permission denied
Failed to mount '/dev/sdb1': Permission denied

```

---

### Post by mtxcoll on 2007-11-15
Gah, never mind, I found out that I had set permissions for ntfs-3g to user, so I typed in this:

```

$ sudo chown root /bin/ntfs-3g
$ mount /media/seagate

```

And got the drive to mount. I still can't mount or unmount the drive as a normal user, however. Any suggestions on how to do that?

```


$ mount /media/seagate
fusermount: user has no write access to mountpoint /media/seagate
FUSE mount point creation failed
Unmounting /dev/sdb1 (SEAGATE)
$ chmod a+w /media/seagate
chmod: changing permissions of `/media/seagate': Operation not permitted
$ sudo chmod a+w /media/seagate
$ mount /media/seagate
fusermount: option allow_other only allowed if 'user_allow_other' is set in /etc/fuse.conf
FUSE mount point creation failed
Unmounting /dev/sdb1 (SEAGATE)
$ gedit 
$ sudo gedit /etc/fuse.conf

$ mount /media/seagate
fusermount: option blkdev is privileged
FUSE mount point creation failed
Unmounting /dev/sdb1 (SEAGATE)


```

---

### Post by glenstewart on 2007-11-20
From [http://www.cheeming.com/blog/index.php](http://www.cheeming.com/blog/index.php), it's recommended:

> I remember I did a lot of research and still did not manage to find out why. But I did find some instructions on how I can resolve it. First do the following:

ls -lh /dev/mapper

If your partition is indicated there, it means its busy. It might look something like the following:

total 0
crw-rw---- 1 root root  10, 63 2007-11-13 06:09 control
brw-rw---- 1 root disk 254,  0 2007-11-12 22:10 sda1
brw-rw---- 1 root disk 254,  1 2007-11-12 22:10 sda5
brw-rw---- 1 root disk 254,  2 2007-11-12 22:10 sda6

Then do the following:

dmsetup remove_all

And try again! Good luck!

---

