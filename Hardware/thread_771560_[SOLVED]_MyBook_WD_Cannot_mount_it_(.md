---
title: "[SOLVED] MyBook WD Cannot mount it :("
date: 2008-04-27
forum: Hardware
---

### Post by stevoo on 2008-04-27
Well i left home all working come back and my external disk could not be mounted. 

After some tweaking i found out that my girl accidently unpluged the hard disk as it was working.

I tried mounting the hard disk on both Ubuntu and Vista and it will not be displayed.

mount will display me this
```
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

Can i get some help in trying to find what the problem it  ? 

please

sTEvoo

---

### Post by edwebdev on 2008-04-27
When you connect the disk and it powers up, does it indicate more/less activity than you remember it indicating before your troubles? Does it make any unusual sounds that it didn't make when it was working properly?

---

### Post by stevoo on 2008-04-28
actually it doesnt make any sound. It is like the hard disk is  not found and doesnt even  try to mount or anything.

Power Led goes on, but absolutely no activity.

It used to spin but now nothing 

Also :
fdisk -l 
returns nothing

cat /etc/fstab
```
proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=5eac5548-51b4-4a91-996b-c0b87f062fe0 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=07D7-070A /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=90884964884949C4 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sda5 :
UUID=07D7-070A /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda3 :
UUID=1c9cc157-5e46-4952-b55d-4fe62489039b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

```

ls -la media
[CODE]
total 48
 0 lrwxrwxrwx 1 root root        6 2007-07-17 23:49 cdrom -> cdrom0
 4 drwxr-xr-x 2 root root     4096 2007-07-17 23:49 cdrom0
16 drwxrwx--- 2 root plugdev 16384 1970-01-01 01:00 sda1
12 drwxrwx--- 1 root plugdev 12288 2008-04-18 17:53 sda2
16 drwxrwx--- 2 root plugdev 16384 1970-01-01 01:00 sda5
{/CODE}

It is like itsdead :(

---

