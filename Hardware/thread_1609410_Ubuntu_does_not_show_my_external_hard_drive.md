---
title: "Ubuntu does not show my external hard drive"
date: 2010-10-30
forum: Hardware
---

### Post by AKG_8 on 2010-10-30
Hi all,

When I plug in my external hard drive, I am not able to see it .. may be Ubuntu is not recognizing it .. Please help

Thanks

AKG

---

### Post by IcarusR on 2010-10-30
Un plug drive, wait a minute, plug in again & in from a terminal run

```
dmesg | tail
```

Is there any mention of it ? Any errors ?

```
sudo fdisk -l
```

Is it listed ?

What is the filesystem ? ext3/4, fat 32, ntfs

Did it ever work ?

Was it correctly 'ejected' when last used ?

Have you tried mounting it manually from a terminal, if so was there an error ?

---

### Post by AKG_8 on 2010-10-30
wow .. somehow it worked this time .. I did need to not do anything ..

Thanks for your response .. Can you tell me how can I mount it manually from the terminal ..

Best

AKG

---

### Post by IcarusR on 2010-10-30
Run

```
sudo fdisk -l
```

Find drive  denotion /dev/sxx & filesystem.

Assuming it is ntfs & /dev/sdc to be mounted at /home/fred/external user & group fred

```
sudo mount -t ntfs -o uid=fred,gid=fred  /dev/sdc /home/fred/external
```

uid & gid needed to maintain ownership as mount is run as root.

See the mount manual

```
man mount
```

Obviously the mount point must exist & you must have write permissions.

---

