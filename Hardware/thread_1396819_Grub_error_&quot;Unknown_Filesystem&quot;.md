---
title: "Grub error &quot;Unknown Filesystem&quot;"
date: 2010-02-02
forum: Hardware
---

### Post by Sedio on 2010-02-02
I just recently installed Ubuntu netbook remix alongside my windows 7.  Everything was working fine until I reallocated memory in a partition.  So now that partition is unallocated memory and when I rebooted the computer came up with this:

    > error: unknown filesystem
    grub rescue >I am completely lost at this point because I tried Super Grub Disk to try and fix the issue but when I tried to fix Grub it just froze and didn't do anything after (at least it didn't seem to).  I ran ubuntu netbook remix again on a live usb and tried to reinstall it like some websites said but it didn't work (though I don't know if I did it correctly).  When I am in ubuntu live usb I run fdisk -l and get:
> 
    Disk /dev/sda: 160.0 GB, 160041885696 bytes
    255 heads, 63 sector/track, 19457 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x3f055986

       Device Boot      Start        End     Blocks   Id   System
    /dev/sda1               1       1959   15728640   27   Unknown
    /dev/sda2   *        1959       1972     102400    7   HPFS/NTFS
    /dev/sda3            1972      10710   70188658    7   HTFS/NTFS
    /dev/sda4           10711      19458                                           70260918+   f   W95 Ext'd (LBA)
    /dev/sda5           10711      16648   47696953+  83   Linux
    /dev/sda6           16649      16907    2080386   82   Linux swap/Solaris

Any help would be greatly appriciated.  I am not that great with linux but I will do my best to get any more information you guys might need!

Thanks!

---

### Post by sooperspook on 2010-05-25
I'm getting the same error on my netbook.

i don't dual boot my net book but I was trying to install 10.04 when I got the same error:
Grub error Unknown Filesystem

I tried booting from the Live Usb but I just get the same message.

Anyone know what to do?

---

