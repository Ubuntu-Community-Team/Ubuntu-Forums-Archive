---
title: "External Hard Drive"
date: 2009-02-21
forum: Hardware
---

### Post by Testrum on 2009-02-21
Hello I'm trying to mount my buddie's external hard drive so I can pull my music and anime collection off it and I've run into this error:
[img]http://i39.tinypic.com/2pr6yjr.png[/img]

I've used this command:
```
sudo fdisk -l
```

and it came up with this report:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cf55f92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18750   150609343+  83  Linux
/dev/sda2           18751       19457     5678977+   5  Extended
/dev/sda5           18751       19457     5678946   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS
```

Any ideas? It's showing it in my list of USB devices as "Optimus Prime In Disguise" since that's what he's named his External Hard Drive :p

---

### Post by dzark on 2009-02-21
Its because it wasn't 'Safely Ejected' in windows... Either plug it back into a windows box and nicely eject, or:

Use the command the error prompt tells you to
```

sudo mount -t ntfs-3g /dev/sdc1 /media/optimus -o force
```

The '-o force' at the end forces mounting, even if the clean unmount flag hasn't been set..

I've never understood why there isn't a button on that dialog saying 'Damn the icebergs! Full steam ahead! Mount my drive anyway!"

---

### Post by Testrum on 2009-02-21
> **dzark said:**
> Its because it wasn't 'Safely Ejected' in windows... Either plug it back into a windows box and nicely eject, or:

Use the command the error prompt tells you to
```

sudo mount -t ntfs-3g /dev/sdc1 /media/optimus -o force
```

The '-o force' at the end forces mounting, even if the clean unmount flag hasn't been set..

I've never understood why there isn't a button on that dialog saying 'Damn the icebergs! Full steam ahead! Mount my drive anyway!"Ah, I see. Thanks!

I didn't want to just input the command cause my buddy use's it for school and has a ton of important stuff on it lol.

---

### Post by dzark on 2009-02-21
If it's important he should be safely ejecting ;)

---

### Post by Testrum on 2009-02-21
> **dzark said:**
> If it's important he should be safely ejecting ;)Yes he should be lol.

---

