---
title: "Help with erasing DDO"
date: 2008-12-22
forum: Hardware
---

### Post by torp74 on 2008-12-22
I have an older Maxtor IDE 160GB drive that I want to use as an external drive in my system. This drive was previously used with a bios that had a 32GB maximum drive size, so I used MAXBLAST to install a DDO onto the drive, allowing me to access the entire drive. I no longer have the old system, just kept the drive. So I purchased an enclosure, installed the drive and plugged it into the USB bus. It came up as a 32GB drive. I have done everything I can to try and erase the MBR so I can access the entire drive but no joy. I have tried gparted, maxblast, seatools, Boot&Nuke, etc. Most of the programs cannot see the drive on the USB bus. I have even tried zeroing the drive out, but I still only get 32GB. Oh yeah, the jumper has been removed so that is not the issue. So, can anybody tel me what I can do to erase this DDO, short of buying an adapter so I can install the drive into my SATA system? I would appreciate any assistance.

Regards,

torp74

---

### Post by prshah on 2008-12-22
> **torp74 said:**
> so I used MAXBLAST to install a DDO onto the drive, 

A dynamic drive overlay is essentially software installed to the boot sector, so that it loads before anything else. To backup and wipe this out, use the below commands```
sudo dd if=/dev/sdd of=/root/orig_mbr bs=446 count=1
sudo dd if=/dev/zero of=/dev/sdd bs=446 count=1
``` replace /dev/sdd with the actual device id of the usb enclosure-d hdd. (You can find it by plugging in the hdd and studying the output of "dmesg | tail".

If you would also like the partition table wiped out, use 512 in place of  466 in the command above.

Once you have done this, you have to "reload" the partition information in the kernel. ```
sudo partprobe /dev/sdd
```

Note that the example device is sdd, and not sdd1 or so; if you add the number it will refer to a partition, which is not connected with the MBR (and hence the DDO software) in any way. Don't forget to replace sdd with the actual device id in your case! Make sure the drive is unmounted!

If you are not careful with the dd command you can INSTANTLY lose a lot of data; so you do this at your own risk, in any and every case!

---

### Post by torp74 on 2008-12-26
> **prshah said:**
> A dynamic drive overlay is essentially software installed to the boot sector, so that it loads before anything else. To backup and wipe this out, use the below commands```
sudo dd if=/dev/sdd of=/root/orig_mbr bs=446 count=1
sudo dd if=/dev/zero of=/dev/sdd bs=446 count=1
``` replace /dev/sdd with the actual device id of the usb enclosure-d hdd. (You can find it by plugging in the hdd and studying the output of "dmesg | tail".

If you would also like the partition table wiped out, use 512 in place of  466 in the command above.

Once you have done this, you have to "reload" the partition information in the kernel. ```
sudo partprobe /dev/sdd
```

Note that the example device is sdd, and not sdd1 or so; if you add the number it will refer to a partition, which is not connected with the MBR (and hence the DDO software) in any way. Don't forget to replace sdd with the actual device id in your case! Make sure the drive is unmounted!

If you are not careful with the dd command you can INSTANTLY lose a lot of data; so you do this at your own risk, in any and every case!

Thanks for this answer. I have used these commands with my local drive added /dev/sdb and I still have no joy. After a reboot, and running fdisk, I still see a drive of 33.8gb in size. Any other ideas?

Regards,

torp74

---

### Post by prshah on 2008-12-26
> **torp74 said:**
> I have used these commands with my local drive added /dev/sdb and I still have no joy

Can you post a gparted (System-Administration-Partition Editor) screenshot?

---

### Post by torp74 on 2008-12-26
> **prshah said:**
> Can you post a gparted (System-Administration-Partition Editor) screenshot?

Gparted screenshot is attached.

---

### Post by prshah on 2008-12-27
> **torp74 said:**
> Gparted screenshot is attached.

Considering that it says disklabel is unrecognized (as it should be for a blank, unpartitioned drive), I'd say that the drive is blanked out successfully, and DDO is not active. Perhaps you need to check the jumper positions carefully. Also note that rarely, the jumper itself may be faulty; use another one, or use a multimeter to check the continuity.

Can't think of anything beyond this.

---

