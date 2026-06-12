---
title: "Can't mount USB flash drive"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by INVICTRA on 2007-02-02
I got a motorola E1070 and a microSD 1GB in it. Ubuntu finds it and I try to mount it :confused:  .... I go in as root :confused:  ....it says it's stupid, help urself :confused: 

with dmsg I get this 

> [17188155.424000] scsi2 : SCSI emulation for USB Mass Storage devices
[17188155.424000] usb-storage: device found at 5
[17188155.424000] usb-storage: waiting for device to settle before scanning
[17188161.520000]   Vendor: Motorola  Model: Motorola Phone    Rev: 2.31
[17188161.520000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17188161.656000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
[17188161.664000] sda: Write Protect is off
[17188161.664000] sda: Mode Sense: 0b 00 00 08
[17188161.664000] sda: assuming drive cache: write through
[17188161.684000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
[17188161.692000] sda: Write Protect is off
[17188161.692000] sda: Mode Sense: 0b 00 00 08
[17188161.692000] sda: assuming drive cache: write through
[17188161.692000]  sda: sda1
[17188161.748000] sd 2:0:0:0: Attached scsi removable disk sda
[17188161.748000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17188161.748000] usb-storage: device scan complete
[17188303.664000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17188303.664000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17188303.664000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount op tion errors=recover not used. Aborting without trying to recover.
[17188303.664000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS vo lume.
invictra@nakhti:~$


I'm a beginer at linux but USB storage devices should work without problems right ?  :tongue:

---

### Post by scrooge_74 on 2007-02-02
i think it has to be fat32 for it to be able to mount it and your seems to say it is ntfs

---

### Post by INVICTRA on 2007-02-02
Why is it saying that? I thought NTFS file systems are inposible on flash drives and other USBflash drive like devices.  :-s

I can try it.

No, didn't work :cry:

---

### Post by INVICTRA on 2007-02-07
Problem solved.

I have ubuntu 6.10 now. Evrything works automaticaly  :)

---

