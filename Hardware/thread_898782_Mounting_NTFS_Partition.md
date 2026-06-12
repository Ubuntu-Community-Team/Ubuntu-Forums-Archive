---
title: "Mounting NTFS Partition"
date: 2008-08-23
forum: Hardware
---

### Post by Juanchi1984 on 2008-08-23
Hi guys, I need help. Excuse me for my English. I have a problem mounting my Windows partition on Ubuntu 8.04. It was working fine since I installed hardy, but one day it stop. When I try mount manually the partition I receive this message

sudo mount -t ntfs /dev/sda1 /media/Windows

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


I have also tried fixing the volume several times through windows chksdk /f. Any idea what may be causing this?

Thanks,


Juanchi

---

### Post by libra1780 on 2008-08-24
try "-t ntfs-3g" as type.. it works on more ntfs types and *should* grant write access

---

### Post by Juanchi1984 on 2008-08-24
Thanks for the reply. I obtain the same error using ntfs-3g.



Update:

I remove ntfs-3g driver with synaptic... then sudo mount -t ntfs /dev/sda1 /media/Windows and it work, but just only read as root. Any idea??

Thanks,

Juanchi

---

### Post by libra1780 on 2008-08-24
you need to set the usermask like on fat systems to access as user
found in man
>        uid=value, gid=value and umask=value
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.

so on mount you have to set
```
 sudo mount -t ntfs /dev/sda1 /media/Windows -o exec,rw,umask=000
```
rw for read/write

---

### Post by Juanchi1984 on 2008-08-24
Thanks for the help libra :). I can access the partition with my user but cant write. I think that is because Im using ntfs instead ntfs-3g.

---

### Post by libra1780 on 2008-08-25
yes, ntfs is said to be read only, ntfs-3g should be RW and should also support more ntfs types, *should*

you are welcome

---

### Post by vanadium on 2008-08-25
> I have also tried fixing the volume several times through windows chksdk /f.
Make sure that you succeed in repairing the disk under MS Windows. Then there shouldn't be any problem mounting it in Ubuntu.

Also make sure that your windows system is fully shut down (no hibernate or stand-by) before accessing the ntfs volume under Ubuntu. This is because the ntfs volume needs to be properly closed by Windows before you can access it (safely) under Ubuntu.

---

### Post by Juanchi1984 on 2008-08-25
I did all that you say vanadium and nothing happened. ntfs works but ntfs-3g don't. Does ntfs-3g support Windows Vista SP1??

---

### Post by vanadium on 2008-08-26
I do not know, really. It might be possible indeed that Vista changed the ntfs format to the extent that it is not anymore supported by current ntfs-3g, but I did not hear reports about that before this.

---

### Post by shane19174 on 2008-08-26
I honestly don't know how to fix the problem you're having (maybe a hardware problem?), but I can say for sure that NTFS partitions created with Vista SP1 (including the boot partition) can still be mounted, read, and written to under Ubuntu. I do it every day.

Sorry I can't really help, but at least you know where not to look for the problem.

---

