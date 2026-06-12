---
title: "Unable to change permissions on 2nd harddrive"
date: 2008-10-31
forum: Hardware
---

### Post by Josueped on 2008-10-31
After upgrading to Intrepid screwed up I did a fresh install, with all my data backed up on a second harddrive. I have done this before.

As I have done in the past I ran gksudo gedit /etc/fstab. I added the line.

/dev/sdb1       /Data           vfat, defaults 0 1

Then ran

```
sudo mkdir /Data
sudo mount -a
df -h
```

So far so good. But when I tried to chown to me, it said operation not permitted. So I ran gksudo nautilus, tried there. No luck. I tried chmod 777, no luck.

I then ran sudo umount /Data  when back to fstab and changed it to

/dev/sdb1       /Data           vfat, auto,rw,user 0 1

Remounted it. No luck. Restarted the computer, no luck. It mounts but everything is read only. I have had this problem before but cannot remember how I fixed it

---

### Post by Josueped on 2008-10-31
Bump

---

### Post by Josueped on 2008-10-31
Got the following outputs, but no luck

sudo blkid

/dev/sdb1: LABEL="M-:M-}oM-jM-wM-:M-VYM-sM-^_k" UUID="4422-EB37" TYPE="vfat" 

mount

/dev/sdb1 on /Data type vfat (rw,noexec,nosuid,nodev)

cat /etc/fstab

/dev/sdb1       /Data           vfat, auto,rw,user 0 1

ls -l /Data

total 16
drwxr-xr-x 14 root root 16384 2008-01-21 13:57 Documents

EDITED TO ADD: I fixed my own problem. Stupid mistake. It is a FAT32 partition, not a linux native. D´oh Needed
/dev/sdb1      /Data  vfat uid=1000,gid=1000,umask=007 0 2

Instead i the fstab

---

