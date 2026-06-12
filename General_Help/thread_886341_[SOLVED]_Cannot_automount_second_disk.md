---
title: "[SOLVED] Cannot automount second disk"
date: 2008-08-11
forum: General Help
---

### Post by b9k9kiwi on 2008-08-11
I have read the automount instructions available in this forum which tell me that adding either;

/dev/sdb1 /media/disk ext3 defaults,umask=007,gid=46 0 0

or

UUID number /media/disk ext3 defaults,umask=007,gid=46 0 0

added to fstab will automount my secondary disk on bootup.

Neither of these options work and I note on re-reading the instructions that they are apparently specific to NTFS volumes.

I would appreciate a pointer as to how I might automount my secondary drive which is a auto-backup target for two other PCs on the network (backups fail, of course, if the volume is not mounted).

AMD Athlon X2 64 4800
Asus M2N ME SX Plus motherboard
Samsung 500Gb HDD Sata (drive a)
Seagate 160Gb HDD Sata II (drive b)
2x1Gb DDR2 667 RAM
nVidia GeForce 6600 256Mb PCIe graphics card

---

### Post by coffeecat on 2008-08-11
> **b9k9kiwi said:**
> Neither of these options work and I note on re-reading the instructions that they are apparently specific to NTFS volumes.

They won't be with 'ext3' in the third field.

First question: what filesystem are you trying to mount, ext3 or fat32? Or something else? Because the 'umask=007,gid=46' options in the fourth field look as though they have come from a line for a fat32 partition.

Next question: have you created the folder /media/disk? Because if you haven't, there's nothing to mount the partition to. And it's probably better to avoid the foldername 'disk'. This is the default name used to automount USB devices. This is not a problem as such - the system will simply generate a mountpoint 'disk-1' (or similar) if you then plug in a USB drive, but you might prefer to use something descriptive. I would choose /media/sdb1 or /media/Data - say.

Anyway, assuming you have created the folder /media/sdb1, and assuming the filesystem to be mounted is ext3, try this:

```
/dev/sdb1     /media/sdb1     ext3    defaults    0 0
```That will mount the partition for read/write by root only. If you want to read-write as an ordinary user, simply create a folder (as root) in it (call it what you want) and then (as root) chown it to your username. (Post back if you don't know how - I'll explain in more detail.) You will then be able to drag/drop/copy/delete in that folder.

That line will perhaps need a little fine-tuning. I'll have a look on my multi-booting machine later and see what I've got there for fstab mounting of ext3 partitions.

---

### Post by jocko on 2008-08-11
You need to tell a little bit about the partition you want to mount.
What's the output of these commands:
```
sudo fdisk -l
```
```
blkid
```
```
cat /etc/fstab
```
That should contain all information needed to make an entry in fstab to automount your partition.

---

### Post by b9k9kiwi on 2008-08-11
> **jocko said:**
> You need to tell a little bit about the partition you want to mount.
What's the output of these commands:
```
sudo fdisk -l
```
```
blkid
```
```
cat /etc/fstab
```
That should contain all information needed to make an entry in fstab to automount your partition.

Beginning of output;

code sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60424   485355748+  83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2a23fef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

code sudo blkid

/dev/sda1: UUID="deb83c33-2a01-40e4-95fb-14aafec92d52" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7b10504b-6fd9-484c-af79-6fff4c329b07" 
/dev/sdb1: UUID="b97d35c4-e54c-415a-9574-0dd108740105" SEC_TYPE="ext2" TYPE="ext3" 

code cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=deb83c33-2a01-40e4-95fb-14aafec92d52 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7b10504b-6fd9-484c-af79-6fff4c329b07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

End of output;

sdb1 mounts manually in /dev/media/disk.

---

### Post by sisco311 on 2008-08-11
add the following line to the fstab:
> UUID=b97d35c4-e54c-415a-9574-0dd108740105 /media/disk ext3 relatime 0 2unmount the partition:
```
sudo umount /dev/sdb1
```create the mount point (if doesn't exist):
```
sudo mkdir /media/disk
```mount the partition:
```
sudo mount -a
```

---

### Post by jocko on 2008-08-11
Yes, what Sisco told you will work, but there may be a problem with mounting it to /media/disk, as this is the place where an unlabled usb device or removable hard drive will be mounted by default. So if you by some reason would mount a removable device before you mount sdb1, the folder would already contain a file system.
Don't know what will happen in that case but at the least it would be annoying.
So it may be better to name the folder /media/sdb1 or /media/whateveryoulike (just make sure to adjust the fstab entry accordingly).

---

### Post by b9k9kiwi on 2008-08-11
> **sisco311 said:**
> 
add the following line to the fstab:
...
[/code]

Thanks, that works just fine.

---

### Post by sisco311 on 2008-08-11
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by b9k9kiwi on 2008-08-11
> **jocko said:**
> Yes, what Sisco told you will work, but there may be a problem with mounting it to /media/disk, as this is the place where an unlabled usb device or removable hard drive will be mounted by default. So if you by some reason would mount a removable device before you mount sdb1, the folder would already contain a file system.
Don't know what will happen in that case but at the least it would be annoying.
So it may be better to name the folder /media/sdb1 or /media/whateveryoulike (just make sure to adjust the fstab entry accordingly).

I noted your comments and so (having succeeded in automounting sdb1 a la Sisco) I plugged in a couple of USB disk devices.

A Seagate 2.5Gb (FAT) pocket hard drive mounted in /media/No Name.

A 61.5Gb (ntfs) external IDE hard drive mounted in /media/61.5 GB Media.

Your advice seems prudent nevertheless so I am happy to put it into practice.

Thanks.

---

