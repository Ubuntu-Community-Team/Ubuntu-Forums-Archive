---
title: "Help with Grub"
date: 2009-06-22
forum: Hardware
---

### Post by mcslave on 2009-06-22
I installed Ubuntu 9.04 and now Grub doesn't give me an option to boot in to Win Vista. I tried adding the entry but it's not working. 

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		790e8fcf-29e1-4cd4-a9d1-6f7cc2bf4829
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=790e8fcf-29e1-4cd4-a9d1-6f7cc2bf4829 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		790e8fcf-29e1-4cd4-a9d1-6f7cc2bf4829
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=790e8fcf-29e1-4cd4-a9d1-6f7cc2bf4829 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		790e8fcf-29e1-4cd4-a9d1-6f7cc2bf4829
kernel		/boot/memtest86+.bin
quiet

title Windows Vista (maybe)
root (hd0,1)
savedefault
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by milton1 on 2009-06-22
Is the entry not functioning, or is it not appearing on your boot menu at all?

---

### Post by mhgsys on 2009-06-22
Try :
```

title Windows Vista (maybe)
rootnoverify (hd0,0)
chainloader +1

```

Instead of 
```

title Windows Vista (maybe)
root (hd0,1)
savedefault
chainloader +1

```

---

### Post by mcslave on 2009-06-22
Well I found out why it wasn't working... Ubuntu deleted both of my partitions during setup. I lost all my files. :(

---

### Post by mcslave on 2009-06-22
Definitely the last time I trust the disc to do the setup for me.

---

### Post by mhgsys on 2009-06-22
ehmz, 

That seems it has to mean you choose to use the entire disk right?
And in that case it's kinda logical it deletes all your partitions and files on that disk.

You have a choice in how it installs.
You can resize the windows disk, use the entire disk or select manual.
I guess you selected use entire disk, and should be more carefull in the future.

---

