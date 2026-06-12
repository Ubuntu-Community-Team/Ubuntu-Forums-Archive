---
title: "The FreeCom external USB Mass Storage Disk cannot be mounted on Edgy"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by rhigan on 2006-11-16
Hi,

I am facing troubles with my IIFreecom 250Go external disk. I cannot mount my NTFS USB External Disk. It seems it cannot be recognized by Edgy.

**Configuration**:
- Laptop Dell Latitude 20Go Internal disk/PentiumII 516Mo Ram
- External USB Hard Disk: IIFreeComm 250 Go NTFS (not FAT32 since I reformat it a while ago for XP)
- Ubuntu Edgy 
- NTFS-3G installed from deb [http://givre.cabspace.com/ubuntu/degy](http://givre.cabspace.com/ubuntu/degy) main-all with a specific pmount
- 2 partition on the Internal Hard Drive: 8Go for XP (NTFS) and 12Go For Linux.* I can see my internal second Windows Partition without any problem.*

I have done the following:

**modprobe usb-storage** is working fine
**modprobe usb-uhci** gives the following error. FATAL: Module usb_uhci not found.

I suspect that the problems comes from "usb_uhci".

How could I know the device from which I can mount the external partition? I have noticed something like /dev/sg0 in the Ubuntu System->Administration-> Device Manager -> 82801 CA/CAM USB Hub 1->UHCI Host Controler -> Classic SLB Hard Drive -> USB Mass Storage  ... 


May be I am missing some important thing? 

Any suggestion would be appreciated. 

Regards, Un saludo, Cordialement 

JAS

---

