---
title: "dual boot and cyliner boundary problems"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by mjd95 on 2008-12-27
I'm new to linux and I recently tried to install Ubuntu 8.10 alongside Vista on an old laptop.  Unfortunately, I ran into a problem almost immediately in finding that whilst ubuntu would boot fine, grub wasn't giving me the option to boot into vista.  I've done some looking around and it seems that I'm not the first to come across something like this, and a solution is to add in some code to /boot/grub/menu.lst telling grub to take vista into consideration.  Currently my menu.lst file looks like this:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d050341d-7a8e-4b26-9c94-857fbe813759
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d050341d-7a8e-4b26-9c94-857fbe813759 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d050341d-7a8e-4b26-9c94-857fbe813759
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d050341d-7a8e-4b26-9c94-857fbe813759 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d050341d-7a8e-4b26-9c94-857fbe813759
kernel		/boot/memtest86+.bin
quiet
```


Also, the ouput from fdisk is:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40bffd7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702        8445    62197756    7  HPFS/NTFS
/dev/sda3            8446        9729    10313730    5  Extended
/dev/sda5            8446        9668     9823716   83  Linux
/dev/sda6            9669        9729      489951   82  Linux swap / Solaris
```

and blkid:

```
/dev/sda1: UUID="66845D75845D48A7" TYPE="ntfs" 
/dev/sda2: UUID="EEB661DBB661A535" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="d050341d-7a8e-4b26-9c94-857fbe813759" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="662c27fe-5006-4640-8a74-33522d840df6" 

```

Now I don't confess to know much about partitioning, and in particular I have no idea what "partition 1 does not end on cylinder boundary" means; but I think I would rather that it did end on the cylinder boundary.  Is it necessary to resolve this before I can go about telling grub to let vista boot?  If so, how do I do this?  Finally, once this is resolved, what code should I actually add to menu.lst to get what I want?

Any help is much appreciated.

Edit - Just saw the absolute beginners forum, sorry if this is in the wrong place.

---

### Post by Pumalite on 2008-12-27
You seem to have a Partition Table problem. But let's try this first: add the frollowing to the end of your menu.lst:

title   Vista
root   (hd0,1)
savedefault
chainloader +1

Reboot and try Vista.

---

### Post by Pumalite on 2008-12-27
If you decide to fix your Partition Table problem; use TestDisk.

---

