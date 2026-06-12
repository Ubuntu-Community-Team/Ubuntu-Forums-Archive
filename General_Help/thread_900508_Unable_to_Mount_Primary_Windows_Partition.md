---
title: "Unable to Mount Primary Windows Partition"
date: 2008-08-25
forum: General Help
---

### Post by Copperteeth on 2008-08-25
Hello everyone, its been awhile since i used ubuntu. Last release i used was 6.10 i think, and my oh my its come a long way. Anyways...

I just installed 8.04 and Im trying to mount my primary Windows Partition. I have 2 hard drives and i am able to mount my 160gig ATA drive but my primary windows partition on my SATA keeps giving me this error
> 
cannot mount volume Invalid mount option when attempting to mount the volume.

I must note that when i installed ubuntu i had no blank cd's so i used UNetbootin. I dont know if that would make a difference.

Also ubuntu is installed on my SATA drive on a 2nd partition.

Thanks for any help in advance.

---

### Post by -Zeus- on 2008-08-25
> **Copperteeth said:**
> Hello everyone, its been awhile since i used ubuntu. Last release i used was 6.10 i think, and my oh my its come a long way. Anyways...

I just installed 8.04 and Im trying to mount my primary Windows Partition. I have 2 hard drives and i am able to mount my 160gig ATA drive but my primary windows partition on my SATA keeps giving me this error


I must note that when i installed ubuntu i had no blank cd's so i used UNetbootin. I dont know if that would make a difference.

Also ubuntu is installed on my SATA drive on a 2nd partition.

Thanks for any help in advance.

please post the command you are using to mount the volume

---

### Post by WRDN on 2008-08-25
You can try manually mounting the disk. In the Terminal, type:

```
sudo fdisk -l
```

This will list all disks and partitions. Find the Windows partition you want to mount. Now, type:

```
sudo mkdir /media/windows
```

If you wish, you can replace "windows" with another name. Finally, type:

```
sudo mount /dev/[device] /media/windows
```

The [device] is listed in the output to "sudo fdisk -l", and it will be either sdaN or hdaN (where N represents a number).

---

### Post by Copperteeth on 2008-08-25
Ah ok now it looks like its mounted properly now. Only question i have now is will this mount automatically on startup?

---

### Post by -Zeus- on 2008-08-25
> **Copperteeth said:**
> Ah ok now it looks like its mounted properly now. Only question i have now is will this mount automatically on startup?

No, it won't.  press Alt+F2 and type "sudo gedit /etc/fstab" and at the bottom, you should input something like this

```
/dev/[device]    /where/you/want/to/mount/it   ntfs   defaults   0  0
```

just make sure that /where/you/want/to/mount/it exists

---

### Post by Copperteeth on 2008-08-25
Well upon looking at my /etc/fstab, i noticed that for some reason the drive was initially being mounted to the cd rom, probably because of the way i installed ubuntu lol. Everything is working now. Thanks a lot for the help.

---

### Post by sisco311 on 2008-08-25
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

