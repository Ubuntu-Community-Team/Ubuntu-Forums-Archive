---
title: "I mounted my sd card but read only?"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by CameronCalver on 2006-08-18
Hello i followed many guides and i am now using card export 2 with my palm tx but for some reason when i put it in my fstab as 
```
/dev/sda1       /mnt/palm     vfat defaults,noauto,owner,rw,uid=cameron,gid=cameron 0
```
when i go mount /mnt/palm (which i should not have to do ) it says
```
[B]cameron@ubuntu:~$ sudo mount /mnt/palm
mount: block device /dev/sda1 is write-protected, mounting read-only
[/B]
```
and when i do 
```
 sudo tail -f /var/log/messages

``` this is what it says
```
device using ohci_hcd and address 14
Aug 18 16:13:42 localhost kernel: [17180825.376000] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 18 16:13:47 localhost kernel: [17180830.388000]   Vendor: Softick   Model: Card Export       Rev: 0001
Aug 18 16:13:47 localhost kernel: [17180830.388000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Aug 18 16:13:47 localhost kernel: [17180830.520000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
Aug 18 16:13:47 localhost kernel: [17180830.528000] sda: Write Protect is on
Aug 18 16:13:48 localhost kernel: [17180830.568000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
Aug 18 16:13:48 localhost kernel: [17180830.580000] sda: Write Protect is on
Aug 18 16:13:48 localhost kernel: [17180830.580000]  sda: sda1
Aug 18 16:13:48 localhost kernel: [17180830.600000] sd 6:0:0:0: Attached scsi removable disk sda
Aug 18 16:13:48 localhost kernel: [17180830.600000] sd 6:0:0:0: Attached scsi generic sg0 type 0

```it says write protect is on how do i turn it off

---

