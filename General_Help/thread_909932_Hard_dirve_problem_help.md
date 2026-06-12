---
title: "Hard dirve problem help"
date: 2008-09-04
forum: General Help
---

### Post by nitro_n2o on 2008-09-04
Hello all, 

my computer is acting so weird! 

fsck fails to check the drive and it won't mount the system. However, the data and the drive are accesibale from a liveCD 

does anybody have hints on fixing this problem? 

Thx

---

### Post by iaculallad on 2008-09-04
> **nitro_n2o said:**
> Hello all, 

my computer is acting so weird! 

fsck fails to check the drive and it won't mount the system. However, the data and the drive are accesibale from a liveCD 

does anybody have hints on fixing this problem? 

Thx

Try to post your:

```
sudo blkid
```

and

```
cat /etc/fstab
```

---

### Post by nitro_n2o on 2008-09-04
I'm currently getting in the system from the root maintenance shell 

blkid looks fine, i'll try to copy as much as possible

/dev/sda1: UUID="long_number" TYPE="ext3" SEC_TYPE="ext3"
/dev/sda2: same stuff different UUID
/dev/sda3: TYPE="swap" UUID="...." 
/dev/sda4: same as sda2


/etc/fstab

it is pretty hard to copy this.. but it seems fine 
it is mounting everything in the right place, but i can't see any data 
for example there is nothing in /home (i have home in a seperate partition)

There is also nothing /usr/local/ (which is in a separate partition also) 
there is also nothing in /initrd ... 

I have no idea what is happening?

```
/var/log/fsck/checkfs says that 
/dev/sda1 contains a file system with errors, check forced. 
Error reading block 4849981 (Attempt to read block from filesystem resulted in (abort read) whlie getting next inode from scan 

/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY

fsck died with exit status 4
```

how to run fsck manully?

---

### Post by nitro_n2o on 2008-09-04
i'm running fsck but and it keeps throwing errors like exepction Emask 0x0 Sact 0x0 sErr 0x0 actoin 0x0  and 
Buffer I/O error on device sda1
status: {DRDY ERR}
error: {UNC}

---

### Post by prshah on 2008-09-04
> **nitro_n2o said:**
> I'm currently getting in the system from the root maintenance shell 
```
/var/log/fsck/checkfs says that 
/dev/sda1 contains a file system with errors, check forced. 
Error reading block 4849981 (Attempt to read block from filesystem resulted in (abort read) whlie getting next inode from scan 
/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY

```


> **nitro_n2o said:**
> i'm running fsck but and it keeps throwing errors like exepction Emask 0x0 Sact 0x0 sErr 0x0 actoin 0x0  and 
Buffer I/O error on device sda1
status: {DRDY ERR}
error: {UNC}

These errors are normal on a dirty (improper shutdown) filesystem and/or on a hard disk that contains bad sectors.

You can keep ignoring the errors, ultimately you will be asked to make fixes, give "y" to every one. (The questions will be interspread with similar error messages as above). Note that you can potentially lose files with this, and, as a corollary, whole filesystems. Unfortunately, there is no other way out, unless you are comfortable with manual debugging (low level hex editing) of the file system.

Also remember to run fsck on UNMOUNTED filesystems, effectively, from the live CD.

To check for (and mark unusable) bad sectors, use```

sudo fsck -c /dev/sda1
``` from live CD terminal; ensure that target filesystem is unmounted.

---

### Post by nitro_n2o on 2008-09-04
Thanks everybody the issue is solved 

apparently fsck didn't like me manually saying 'y' so fsck -y solved it

Thanks again

---

