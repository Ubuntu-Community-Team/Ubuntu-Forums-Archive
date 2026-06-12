---
title: "hard drive docking station advice"
date: 2009-02-05
forum: Hardware
---

### Post by dancavs on 2009-02-05
Im looking to buy a usb hard drive docking station. However the 2 models Ive discovered do not mention wether or not they will work with linux/ubuntu. after googling a bit i am pretty much none the wiser. so My question is does anyone have any experience with these in linux, and if so, what model/brand have they used?

the 2 ive identified are

[Welland's SunBright ME-601J]("http://www.netplus.com.au/products-detail.asp?code=RM21&cat=Removable%20Storage&subcat=Hard%20Drives%20/%20CD%20External%20Cases&pcode=RMEX3.5SATA-ESDK")

[Shintaro Hard Drive Docker SH23SDOCK]("http://www.i-tech.com.au/products/32760_Shintaro_Hard_Drive_Docker_SH23SDOCK.aspx")

---

### Post by teq. on 2009-07-07
I just tried to use the Shintaro dock on my ubuntu (intrepid) setup with no luck

it doesn't even register anything in the log files when I plug it in (dmesg, log/messages etc)

---

### Post by teq. on 2009-07-07
ok ignore that, I just tried two more and they worked fine
what are the chances that the first one of the bunch was DOA huh.

It loads fine, my media browser even popped up with the name of the NTFS disk and showed me all the contents.
These work great!

> Jul  8 09:46:18 brett kernel: [248078.836010] usb 5-5: new high speed USB device using ehci_hcd and address 5
Jul  8 09:46:18 brett kernel: [248078.978149] usb 5-5: configuration #1 chosen from 1 choice
Jul  8 09:46:18 brett kernel: [248079.091177] usbcore: registered new interface driver libusual
Jul  8 09:46:18 brett kernel: [248079.120112] Initializing USB Mass Storage driver...
Jul  8 09:46:18 brett kernel: [248079.120450] scsi4 : SCSI emulation for USB Mass Storage devices
Jul  8 09:46:18 brett kernel: [248079.120628] usbcore: registered new interface driver usb-storage
Jul  8 09:46:18 brett kernel: [248079.120745] USB Mass Storage support registered.
Jul  8 09:46:23 brett kernel: [248084.121158] scsi 4:0:0:0: Direct-Access     Generic  External         2.12 PQ: 0 ANSI: 4
Jul  8 09:46:23 brett kernel: [248084.132386] sd 4:0:0:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Jul  8 09:46:23 brett kernel: [248084.133634] sd 4:0:0:0: [sdb] Write Protect is off
Jul  8 09:46:23 brett kernel: [248084.134512] sd 4:0:0:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Jul  8 09:46:23 brett kernel: [248084.135133] sd 4:0:0:0: [sdb] Write Protect is off
Jul  8 09:46:23 brett kernel: [248084.135367]  sdb: sdb1
Jul  8 09:46:23 brett kernel: [248084.152976] sd 4:0:0:0: [sdb] Attached SCSI disk
Jul  8 09:46:23 brett kernel: [248084.153275] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jul  8 09:48:41 brett kernel: [248222.010790] usb 5-5: USB disconnect, address 5


---

### Post by dancavs on 2009-08-07
yeah well I went and got one - a shintaro and it seems works fine :)

---

