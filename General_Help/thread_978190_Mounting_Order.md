---
title: "Mounting Order"
date: 2008-11-10
forum: General Help
---

### Post by Laibcoms on 2008-11-10
Hi,

Is there a way to control the "order" of the mounted drives?

I have four drives I just named C, D, F, G (these are NTFS), in the file they are correctly in order, however, when opening files or viewing via Nautilus, they are not in order.

Either it is like this: G, C, D, F; or F, G, C, D; or in any other order.

Thanks for the help.

---

### Post by taurus on 2008-11-10
Do you mount those partitions through /etc/fstab?

```
cat /etc/fstab
```

---

### Post by Laibcoms on 2009-02-14
> **taurus said:**
> Do you mount those partitions through /etc/fstab?

```
cat /etc/fstab
```

Hi,

Yes, I have this:
```

/dev/sda1 /media/C: ntfs    defaults,umask=007,gid=46 0       1
/dev/sda5 /media/D: ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb1 /media/F: ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb5 /media/G: ntfs    defaults,umask=007,gid=46 0       1

```

But, for every start-up, the order of the drives are messed-up.

---

### Post by sisco311 on 2009-02-14
Use the UUID to mount the partitions. [uhelp]community/UsingUUID[/uhelp]

Type:
```
sudo vol_id -u /dev/sda1
```in a terminal to find the uuid of the partition.
ex.:> 60C421D0C421A96Cthen edit the fstab entry:
```
gksu gedit /etc/fstab
```to> UUID=60C421D0C421A96C /media/C: ntfs    defaults,umask=007,gid=46 0       1

---

### Post by Laibcoms on 2009-04-04
I switched to UUID after doing a fresh install using Jaunty.  Still experiencing the same - everytime I boot-up there's a chance the order of the NTFS drives changes.

Here's my new fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d84333ef-26af-4dd6-bee7-227dd79e2e4d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=fa07d1a8-b823-47ad-b7a3-a93403557748 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=BCC01853C01815EC /media/C ntfs-3g defaults,locale=en_PH.UTF-8 0 2
UUID=B084D9D684D99EE2 /media/D ntfs-3g defaults,locale=en_PH.UTF-8 0 2
UUID=8E58D05F58D0479B /media/F ntfs-3g defaults,locale=en_PH.UTF-8 0 2
UUID=BE5404F35404B067 /media/G ntfs-3g defaults,locale=en_PH.UTF-8 0 2

```

I seldom see them in the right order I entered in fstab, as "C-D-F-G".

---

### Post by ktamm on 2009-05-18
I am wondering if anyone else has come across a solution to this problem as I'm having a similar issue. Not only are my local hdds doing this but my nfs mounts seem to randomly order themselves as well.

---

