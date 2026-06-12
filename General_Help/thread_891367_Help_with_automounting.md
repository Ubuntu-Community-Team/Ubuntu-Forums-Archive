---
title: "Help with automounting"
date: 2008-08-16
forum: General Help
---

### Post by Laibcoms on 2008-08-16
Hi,

   I need help with automounting, it's weird and can't make sense of what's happening.

Drives/Partitions I am trying to auto-mount:
> 
C: - NTFS - SCSI1 - Boot partition
D: - NTFS - SCSI1 - Partition 2
F: - NTFS - IDE1 - primary partition
G: - NTFS - IDE1 - partition 2


Result of sudo fdisk -l
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb523b523

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       17176    56042752+   f  W95 Ext'd (LBA)
/dev/sda3           17177       19207    16314007+  83  Linux
/dev/sda4           19208       19457     2008125   82  Linux swap / Solaris
/dev/sda5           10200       17176    56042721    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dd2b41f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    7  HPFS/NTFS
/dev/sdb2            4866        9729    39070080    f  W95 Ext'd (LBA)
/dev/sdb5            4866        9729    39070048+   7  HPFS/NTFS


Now, if my setting is like this:
```

/dev/sda1    /media/C:    ntfs-3g    defaults    0    0
/dev/sda5    /media/D:    ntfs-3g    defaults    0    0
/dev/sdb1    /media/E:    ntfs-3g    defaults    0    0
/dev/sdb5    /media/F:    ntfs-3g    defaults    0    0

```

It auto-mounts drives: C; D; and G only.  It won't mount Drive F, which is NTFS - IDE1 - Primary partition (check above)

And if my setting is like this:
```

/dev/sda1    /media/C:    ntfs-3g    defaults    0    0
/dev/sda5    /media/D:    ntfs-3g    defaults    0    0
/dev/sdb1    /media/F:    ntfs-3g    defaults    0    0
/dev/sdb5    /media/G:    ntfs-3g    defaults    0    0

```

It automounts drives: C; D; and E; only.  It won't mount Drive G, which is NTFS - IDE1 - Partition 2 (check above)


I can't make sense of what's happening, anyone can help?

Thanks.  ^_^

---

### Post by iaculallad on 2008-08-16
What about doing it this way:

Then, edit your /etc/fstab file:

```
gksudo gedit /etc/fstab
```

and delete your previous entries w/c automounts your mentioned partitions and replace it with the lines of texts below:

```
/dev/sda1 /media/C:     ntfs    defaults,umask=007,gid=46 0       1
/dev/sda5 /media/D:     ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb1 /media/F:     ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb5 /media/G:     ntfs    defaults,umask=007,gid=46 0       1
```

Save and Close, and on your terminal again:

```
sudo mount -a
```

---

### Post by diwas on 2008-08-16
Why dont u install NTFS Configuration Tool? Its in synaptic.

---

### Post by cariboo on 2008-08-16
To get your internal drives to mount on boot modify /etc/hal/fdi/policy/preferences.fdi

```
sudo gedit /etc/hal/fdi/policy/preferences.fdi
```

You have to modify this line:

```
<merge key="storage.automount_enabled_hint" type="bool">false</merge>
to this:
<merge key="storage.automount_enabled_hint" type="bool">true</merge>
```

Jim

---

### Post by Laibcoms on 2008-08-16
Thanks everyone!  ^_^  Worked, good to know different methods also, something new learned :D

---

