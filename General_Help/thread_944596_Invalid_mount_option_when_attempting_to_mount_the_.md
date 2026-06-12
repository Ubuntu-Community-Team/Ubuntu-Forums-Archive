---
title: "Invalid mount option when attempting to mount the volume."
date: 2008-10-11
forum: General Help
---

### Post by baudday on 2008-10-11
I get that message when trying to access my external hard drive. It spins, but then it gives me that message. I used it on my last installation of Ubuntu which started to run slow, so I backed everything up onto the external drive and reinstalled. I was not expecting to get this message, and would be devistated if all the stuff on there was lost. Does anyone know how I can get my external drive to work? Thanks in advance for any help with this.

---

### Post by jerome1232 on 2008-10-11
Well we can try manually mounting and see what what happens, what file system is the disk? Can you post the output of ```
sudo fdisk -l
```

---

### Post by baudday on 2008-10-11
It's etc3 or something, I forget, but I formatted it with gparted on my last installation, so it really should work.'

Here's the output:

```
Disk /dev/sda: 160.0 GB, 160029999616 bytes
255 heads, 63 sectors/track, 19455 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee81ee81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19078   153244003+  83  Linux
/dev/sda2           19079       19455     3028252+   5  Extended
/dev/sda5           19079       19455     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

```

---

### Post by baudday on 2008-10-11
okay ext3 there we go. However, I just opened gparted, and it thinks it's fat32 and it's mounting it at media/cdrom0 I'm really confused now.

---

### Post by jerome1232 on 2008-10-11
Okay so I take it sdb is the external drive, yes it shows up as fat32 according fdisk.

I'd also like to see your fstab, sorry if I don't respond quickly i'm trying to config dual monitors and it's not working under 8.10 for some reason

```
cat /etc/fstab
```

---

### Post by baudday on 2008-10-11
No problem at all, I'm just glad you're helping me.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=48d73c56-73cd-4690-bdf0-0d6ac0abe3cb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7b26c6bd-4a40-45d5-9b7d-9ebd5f04b91d none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by baudday on 2008-10-11
I know for a fact it should be ext3 not fat32. I'm not sure if this is relevant, but I used a program (I forget the name, it's pretty popular) to emulate a live cd of ubuntu 8.04 on the external drive for my clean install. This could possibly explain why it's mounting it as a cdrom?

---

### Post by jerome1232 on 2008-10-11
Ok see that entry in fstab that says sdb1, you need to remove it, it's telling your system to mount the external drive as a cd-rom, it may have been entered by that program you mentioned.

```
gksu gedit /etc/fstab
```
```
make it look like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=48d73c56-73cd-4690-bdf0-0d6ac0abe3cb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7b26c6bd-4a40-45d5-9b7d-9ebd5f04b91d none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by baudday on 2008-10-11
Awesome! Thank you so much! I could not have done it without your help, I am truly grateful.

---

### Post by MilkeySUFC on 2008-10-12
Yep, thanks from me too. I had same problem with my JVC Everio HDD camcorder.

---

### Post by MidnightWRX on 2008-10-12
Thank you as well on my behalf. Just switched to ubuntu on a new machine, and the learning curve so far has been steep, but fun.

---

