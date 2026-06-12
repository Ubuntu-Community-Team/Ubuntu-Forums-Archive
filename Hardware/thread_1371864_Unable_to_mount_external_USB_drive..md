---
title: "Unable to mount external USB drive."
date: 2010-01-03
forum: Hardware
---

### Post by st_itty on 2010-01-03
I have a WD 500GB MyBook that I have been using as an external drive on my ubuntu server 9.04. It had 2 partitions a FAT32 and XFS and it's been working fine for over a year. Since the XFS partition was getting full I decided to remove the FAT32 and make the whole disk to XFS. So I deleted the FAT32 partition using GParted. After this my computer is not connecting to the USB drive anymore I tried connecting it to the server as well as Ubuntu 9.10 desktop both throws the same error. Doing dmesg I found the following 
[968106.570071] usb 1-1: new full speed USB device using uhci_hcd and address 19
[968121.690074] usb 1-1: device descriptor read/64, error -110
[968136.920128] usb 1-1: device descriptor read/64, error -110
[968137.150068] usb 1-1: new full speed USB device using uhci_hcd and address 20
Doing some search online I came across threads saying this is some issue with the usb driver and so on but my problem is why was it working fine until I deleted the FAT partition. This was my backup drive for all my computers and now I'm really uncomfortable knowing that my back disk is unusable at least for now. Any help would really be appreciated.

---

