---
title: "flash drive won't mount"
date: 2008-08-23
forum: General Help
---

### Post by myr532 on 2008-08-23
my flash drive won't mount anymore.The error message says "Cannot mount volume.Invalid mount option when attempting to mount the volume 'USB DISK'."

the flash drive works just fine in my windows desktop though.

---

### Post by master.swarky on 2008-08-23
Just do like that:
Create a directory 'flash' in your 'media' directory:
```

sudo mkdir /media/flash

```
and then issue a command:
```

sudo mount -t vfat /dev/sdXX /media/flash

```
if you had a FAT filesystem, and 
```

sudo mount -t ntfs-3g /dev/sdXX /media/flash

```
if you had a NTFS filesystem.

Change XX to your flash device address, I suppose it will be sdb1, if you have just one hard drive.

Cheers :)

---

### Post by qstraza on 2008-08-23
if you dont know how to check the name of the device:
```
dmesg | tail -c 2000
```

---

