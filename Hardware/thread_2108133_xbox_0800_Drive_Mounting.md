---
title: "xbox 0800 Drive Mounting"
date: 2013-01-23
forum: Hardware
---

### Post by Sutur on 2013-01-23
Hi ):P

I have an xbox 360 0800 drive installed via sata.

The device is recognised by the system as /dev/sg2.

The device is not automatically mounted, and I cannot mount the drive.

Does anyone know about this sort of thing?

---

### Post by Sutur on 2013-01-23
More info:

```
surt@Eridu:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg2'	rwrw-- : 'PLDS' 'DG-16D2S'
-------------------------------------------------------------------------
```

So should be:

```
sudo mount /dev/sg2 /cdrom
```

Or: 

```
sudo mount -t iso9660 /dev/sg2 /cdrom
```

But I get this:

```
mount: /dev/sg2 is not a block device
```

---

### Post by Sutur on 2013-01-26
Aaaaanybody?

---

