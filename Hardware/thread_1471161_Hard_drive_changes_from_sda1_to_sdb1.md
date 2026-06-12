---
title: "Hard drive changes from sda1 to sdb1"
date: 2010-05-03
forum: Hardware
---

### Post by drstee on 2010-05-03
I have a 1TB HDD in my computer aswell as a 40GB(the one with ubuntu installed on it) and a 160GB (with windows on it, which i only use for ProTools). And i have my 1TB set so it automatically gets mounted upon login. But sometimes it wont mount because its changed from being sda1 to sdb1 when i look in 'fdisk -l' in terminal. I never used to have this problem in 9.10, but i did in 9.04. and the problem has came back in 10.04.
If anyone has got any suggestions i would be very grateful.
Cheers.

---

### Post by oldfred on 2010-05-03
I do not know an answer but are some drives SATA and some PATA or ide. My SATA drives always come up in port order, but I have seen where IDE drives or external drives may not always be the same sdaX.

They may have tried to speed up boot so much that all drives are not up to speed and seen??

---

### Post by tgalati4 on 2010-05-03
This could be a bug in DeviceKit which is now used to enumerate hardware.  HAL has been removed because it was too slow.  But perhaps HAL was working more consistently in mixed hardware environments?

I would search the DeviceKit bugs in launchpad.

The workaround is to write a script that contains mount commands with both device names.  If one fails, the next one should stick.  If the first one mounts, the second will get "already mounted".

It's a rough hack, but then isn't the entire concept of linux a rough hack?

---

### Post by srs5694 on 2010-05-03
How are you auto-mounting the problem disk? If you're using an /etc/fstab entry, you should be able to get it to work consistently by using a UUID rather than a device file entry (/dev/sda1 or whatever). For instance:

```

/dev/sda1   /boot      ext2    defaults      
UUID=1445adc8-3145-4fcb-86df-701f0f711943   /boot      ext2    defaults      

```

Both these lines boot /dev/sda1 (or the disk with UUID 1445adc8-3145-4fcb-86df-701f0f711943) at /boot, using ext2fs. If your system has the first line, you could replace it with the second entry, except that you'll need to adjust the UUID value for the partition you want to mount. You can find the UUID value with the blkid command, as in "blkid /dev/sdb1". Note that your /etc/fstab file should contain just *one* of these lines; I only showed both of them above for illustrative purposes.

---

### Post by tgalati4 on 2010-05-03
True.  UUID's were implemented for precisely this purpose.

---

### Post by drstee on 2010-05-05
> **srs5694 said:**
> How are you auto-mounting the problem disk? If you're using an /etc/fstab entry, you should be able to get it to work consistently by using a UUID rather than a device file entry (/dev/sda1 or whatever). For instance:

```

/dev/sda1   /boot      ext2    defaults      
UUID=1445adc8-3145-4fcb-86df-701f0f711943   /boot      ext2    defaults      

```

Both these lines boot /dev/sda1 (or the disk with UUID 1445adc8-3145-4fcb-86df-701f0f711943) at /boot, using ext2fs. If your system has the first line, you could replace it with the second entry, except that you'll need to adjust the UUID value for the partition you want to mount. You can find the UUID value with the blkid command, as in "blkid /dev/sdb1". Note that your /etc/fstab file should contain just *one* of these lines; I only showed both of them above for illustrative purposes.

Thankyou very much, i will try that later on and get back to tell you if it was successful.

---

### Post by drstee on 2010-05-05
> **drstee said:**
> Thankyou very much, i will try that later on and get back to tell you if it was successful.

Yeh that seems to have worked, nice one mate. much appreciated :-)

---

### Post by drstee on 2010-05-05
> **srs5694 said:**
> How are you auto-mounting the problem disk? If you're using an /etc/fstab entry, you should be able to get it to work consistently by using a UUID rather than a device file entry (/dev/sda1 or whatever). For instance:

```

/dev/sda1   /boot      ext2    defaults      
UUID=1445adc8-3145-4fcb-86df-701f0f711943   /boot      ext2    defaults      

```

Both these lines boot /dev/sda1 (or the disk with UUID 1445adc8-3145-4fcb-86df-701f0f711943) at /boot, using ext2fs. If your system has the first line, you could replace it with the second entry, except that you'll need to adjust the UUID value for the partition you want to mount. You can find the UUID value with the blkid command, as in "blkid /dev/sdb1". Note that your /etc/fstab file should contain just *one* of these lines; I only showed both of them above for illustrative purposes.

Yeh that seems to have worked, nice one mate. 
much appreciated :-)

---

