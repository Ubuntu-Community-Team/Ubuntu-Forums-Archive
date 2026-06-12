---
title: "How to mount a USB Hard Drive"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by yanks0616 on 2006-11-06
I installed ubuntu 6.06 on my old laptop using my CDRom drive. After installing the OS i swapped my CDRom with an DVD/CDRW drive. 

I edited the /etc/fstab file. I was previously working with SUSE linux. 

Now the problem is how to install the USB hard Drive with read write persmission. The USB hard drive mounts i only read mode. 

Any suggestion and help will be deeply appreciated.

---

### Post by taurus on 2006-11-06
Is it NTFS, FAT32/VFAT, ext3, etc.?  And how do you mount it?

---

### Post by yanks0616 on 2006-11-07
It is NTFS format. Is there a way i can format it in fat32 from windows xp as when i try to format it it gives me only NTFS as an option.

---

### Post by pitkali on 2006-11-07
> **yanks0616 said:**
> It is NTFS format. Is there a way i can format it in fat32 from windows xp as when i try to format it it gives me only NTFS as an option.
That's weird but not unheard of - my girlfriend had the same issue. I suggest formatting under linux. Just install the package dosfstools and then run:
```
mkfs.vfat -F32 /dev/sda1
```
This assumes your internal hard drive is IDE (and not SATA for instance). Otherwise you will most probably want to use /dev/sdb1 (note: usb drives are seen by the system as scsi devices.) You may check the name of the drive by finding your USB drive in the output of command dmesg (after connecting it to the computer that is.)

Regards,

---

