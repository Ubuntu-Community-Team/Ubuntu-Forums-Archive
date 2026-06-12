---
title: "External HD not always recognised at start up"
date: 2014-09-08
forum: Hardware
---

### Post by Robbyx on 2014-09-08
Is there anything I can do to ensure that the external HD gets mounted upon startup? Often I get a message that the partition is not ready and I have to wait. Sometimes it loads sometimes, like just now, it would not load so I skipped it and later loaded all drives with mount -a. With the mount -a the External HD mounted.

This is the entry in fstab:

> #/dev/sdd2:
UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6  /media/xhd_system_data ext4 relatime 0 0
#/dev/sdd3: 
UUID=c99be12f-3a2d-4411-ab7c-5696167482dc /media/xhd_old_bacs ext4 relatime 0 0
# /dev/sdd4
UUID=84a9cb0b-6006-4996-8b4a-2edc07cc25c4 /media/spare4 ext4 relatime 0 0

Robin

---

### Post by TheFu on 2014-09-08
Your fstab settings tell it to wait. Why?  **man fstab** explains the numbers at the end - so it doesn't get stuck waiting.

You can also stop using the fstab for mounting external drives and use autofs.  Then the storage won't be mounted until used.

Or you can manually mount those later in a script that is run last out of init.d/ .... your choice. Lots of options.

---

### Post by Robbyx on 2014-09-09
> **TheFu said:**
> 
UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6 /media/xhd_system_data ext4 relatime 0 0

Your fstab settings tell it to wait. Why?  **man fstab** explains the numbers at the end - so it doesn't get stuck waiting.


Which entry gives the instruction to wait? It can not be the 6th entry because the manual says

> If the sixth field is not present or zero, a value of zero is returned and fsck will assume that  the      filesystem does not need to be checked.

Robin

---

### Post by Robbyx on 2014-09-09
I have just installed atofs. Should I take the external HD  out of fstab? I also have an ssd drive that contains my root, home, data1, data2, swap. I assume they should remain in fstab or should the data1 and data2 come out of fstab as well?

If you suggest I leave them in, should i change the 4th field to include noauto?

Robin

---

### Post by TheFu on 2014-09-09
>        The sixth field (fs_passno).
              This field is used by the fsck(8) program to determine the order
              in which filesystem checks are done at reboot  time.   The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2.  Filesystems within  a
              drive will be checked sequentially, but filesystems on different
              drives will be checked at the same time to  utilize  parallelism
              available in the hardware.  If the sixth field is not present or
              zero, a value of zero is returned and fsck will assume that  the
              filesystem does not need to be checked.


So - looks like the zero should ignore fsck - for some reason I thought it controlled the order that things were mounted - it does not. I need to RTFM more myself. ;) Sorry for the confusion and mistake.

---

### Post by TheFu on 2014-09-09
> **Robbyx said:**
> I have just installed atofs. Should I take the external HD  out of fstab? I also have an ssd drive that contains my root, home, data1, data2, swap. I assume they should remain in fstab or should the data1 and data2 come out of fstab as well?

If you suggest I leave them in, should i change the 4th field to include noauto?

Robin

Hopefully, you installed **autofs**. ;)   No fstab is desired for this method of mounting.  

Storage that needs to be mounted at boot time, must use the fstab.  /home is NOT one of those things, and most data partitions are not either. swap and / (/var, /bin, /sbin )  and /boot are.  /usr shouldn't need to be mounted.  There is a [specific agreement between all POSIX UNIX operating systems]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for what must be available at boot and what can wait. That link is for Linux, but mostly follows the UNIX standard.

---

