---
title: "nokia n91 symbian 9.1 how to mount?"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by naseem on 2007-02-11
hi i'm tring to access my nokia n91, I found out that it's not possible to do it via bluetooth since the    phone does not install the nfsapp-5.19-series60.v2.sis file neaded for the connecion.
So i'm tring with the usb connection, lsusb shows it
```
Bus 002 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0421:0444 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```
but now what do I have to do to access it?

---

### Post by naseem on 2007-02-12
up:)

---

### Post by naseem on 2007-02-14
anyone?
I read in a 3d that the n91 shows up as a usb disk when pluged in, it does not happen to me, is it a kernel problem? I have a 2.6.17-10-generic

---

### Post by abattoir on 2007-02-24
Hi. Yes, It does indeed show up as a USB Mass storage device. Make sure you select 'Mass Storage' when your phone prompts you after you connect it with your PC. I don't think it's a kernel problem as it worked fine for me when i was using that kernel. Bluetooth also works fine, so i can browse the phone's filesystem using OBEX file transfer.

---

### Post by 5T5 on 2007-06-04
> **naseem said:**
> hi i'm tring to access my nokia n91, ... 
For N91 you will better of with SymSMB.
That will do wireless file share/file access for Series 60 3rd edition phones.

---

