---
title: "ORICO 5 Port USB3.0 PCI-E Expansion Card not working"
date: 2020-01-06
forum: Hardware
---

### Post by West Swan on 2020-01-06
Hello,


I have an ORICO 5 Port USB3.0 PCI-E Expansion Card with Dual Chip with the Part Number  PVU3-5O2I-V1

The 5 USB Ports work in Windows 10 but not in Lubuntu 19.10

I used "lspci" to check if the expansion card are being recognized, and it gave me the following result (hopefully it comes through in a code box if I have done it right):

```
 

0b:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)   


```                     

 
I assume that is the Orico device as all the other entries were AMD (I have an AMD motherboard).       [/LEFT]
  and with lsusb I get:                      

 
```
 

Bus 009 Device 004: ID 0bda:58ba Realtek Semiconductor Corp. 

Bus 009 Device 003: ID 0572:141b Conexant Systems (Rockwell), Inc.  

 Bus 009 Device 002: ID 0451:8044 Texas Instruments, Inc. 

Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 010 Device 002: ID 0451:8046 Texas Instruments, Inc. 

Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 008 Device 003: ID 0bda:0321 Realtek Semiconductor Corp. 

Bus 008 Device 002: ID 2109:0813 VIA Labs, Inc. USB3.0 Hub

Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 007 Device 003: ID 2109:2813 VIA Labs, Inc.
 
 Bus 007 Device 002: ID 2109:3431 VIA Labs, Inc. Hub

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 003 Device 003: ID 1e71:170e NZXT NZXT USB Device

Bus 003 Device 002: ID 0b05:18f3 ASUSTek Computer, Inc. 

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 001 Device 004: ID 8087:0029 Intel Corp. 

Bus 001 Device 005: ID 1a7c:0191 Evoluent VerticalMouse 4

Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub

Bus 001 Device 002: ID 05af:1019 Jing-Mold Enterprise Co., Ltd USB Keyboard

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                   

```



Can anyone assist please?  I have googled this the last couple of days and read different forum posts but have no idea what to do.


 Regards,



 Paul

---

### Post by West Swan on 2020-01-06
Sorry about the blank code boxes and formatting.  Not sure what I did wrong.

---

### Post by guiverc on 2020-01-08
I don't have any ideas/solutions, however to avoid assumptions in knowing which device it is, did you compare the `lspci` and esp. `lsusb` output of without & with it attached?  Assumptions are best avoided.

---

### Post by West Swan on 2020-01-08
Oh you mean pull the card out then run those commands again in the terminal?

I'll try and get back.

---

### Post by West Swan on 2020-01-08
I just checked and it is definitely the Via VL805.

---

### Post by West Swan on 2020-01-16
Bump - I've tried everything I can research to get this Orico card working.  Can anyone assist please.

---

### Post by jorgemarmo on 2020-09-26
Hi, 
Any solution?

I came to this very same problem today

---

### Post by rbmorse on 2020-09-26
There was a thread on one of the Arch boards about this piece of kit...the solution appears to be a firmware update which is available from VIA but requires Windows to install.

---

### Post by jorgemarmo on 2020-09-27
I updated firmware on winXP, did the power off cycle, re-read the new firmware version 13704, so update was ok and the card is still not working....

---

### Post by jorgemarmo on 2020-09-27
I just tried these lines on grub conf file as suggested in older posts 
```

GRUB_CMDLINE_LINUX="iommu=soft"
GRUB_CMDLINE_LINUX="intel_iommu=off"
```

and
```

GRUB_CMDLINE_LINUX="iommu=soft"
GRUB_CMDLINE_LINUX="intel_pci=nomsi"

```

and still not working

---

