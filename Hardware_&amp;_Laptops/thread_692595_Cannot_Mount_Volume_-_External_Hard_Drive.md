---
title: "Cannot Mount Volume - External Hard Drive"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by Daniel591992 on 2008-02-09
Hey, someone lend me a hand...

```
Cannot mount volume.
$LogFile indicates unclean shutdown(0,0) failed to mount '/dev/sda1': operation not supported Mounted is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown windows cleanly. Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda1 /media/My Book -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 /media/My Book ntfs-3g defaults, force 0 0
```

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
```

I would go back to safely remove it, but accidently deleted Windows (WHOOPS!). Thankfully, I still have 10 days under my Laptop's warranty, so I'll be getting some recovery disks.

Another question. Will it be possible for me to have Linux installed and Dual Boot Windows (installing Windows second). Or is there a way for me to somehow burn all of my Ubuntu stuff so I don't have to start from scratch if I uninstall Ubuntu, Install Windows, then dual boot Ubuntu (I'd prefer to do this). Send me a PM if you know this since it's off-topic. :)

Thanks.

---

### Post by jan quark on 2008-02-11
hey 

I do not like answering question via PM because everybody should benefit from them

so to the first issue unsafe shutdown says it all
and no windows to boot into it and safely shutdown again is rather unfortunate 


you can dual boot with windows and ubuntu of course

but when you install windows as the second OS then you have to manually restore the Grub loader

the easiest way is to install windows first, create an additional blank partition, and then boot the Ubuntu CD and install, choosing the option install on largest continuous free space

here is a good dual booting site, explaining the procedure of many dual-booting variants

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)


and what files do you want to back up

some private files like music and documents 
or system configuration files, the whole ubuntu files so to speak ?

---

