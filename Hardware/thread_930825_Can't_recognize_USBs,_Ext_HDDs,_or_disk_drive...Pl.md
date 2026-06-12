---
title: "Can't recognize USBs, Ext HDDs, or disk drive...Please help"
date: 2008-09-26
forum: Hardware
---

### Post by Cjmkee on 2008-09-26
I have recently installed Ubuntu Hardy from a CD that a friend in the IT department gave me. Everything seems to be working fine except it doesn't recognize my USB ports. I plug memory sticks and my Ext HDD (a Western Digital Passport) into the USB and nothing happens. When I go to Terminal and use the command lsusb I get this...

chris@chris-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
chris@chris-laptop:~$

Also...I thought I might have gotten a bad copy of Ubuntu so I went to the website and downloaded the .iso file. When I opened CD/DVD Creator to burn it to a CD so I could try to reinstall CD/DVD Creator does not detect the CD in the CD drive.

Can anyone help

---

### Post by sisco311 on 2008-09-26
Plug out the external hard and plug it in.
Open a terminal and post the output of:
```
dmesg | tail -n 20
```
and
```
sudo fdisk -l
```

---

### Post by Cjmkee on 2008-09-26
dmesg | tail -n 20 
    
    chris@chris-laptop:~$ dmesg | tail -n 20
[ 9895.790258] usb 4-4: new high speed USB device using ehci_hcd and address 44
[10949.703071] usb 4-4: new high speed USB device using ehci_hcd and address 54
[10950.227445] usb 4-4: new high speed USB device using ehci_hcd and address 58
[10951.913335] usb 4-4: new high speed USB device using ehci_hcd and address 72
[10957.955050] usb 4-4: new high speed USB device using ehci_hcd and address 112
[10962.148229] usb 4-4: new high speed USB device using ehci_hcd and address 126
[ 3868.181565] usb 4-4: new high speed USB device using ehci_hcd and address 4
[10966.132954] usb 4-4: new high speed USB device using ehci_hcd and address 10
[10967.066780] usb 4-4: new high speed USB device using ehci_hcd and address 21
[10967.271905] usb 4-4: new high speed USB device using ehci_hcd and address 22
[10967.600226] usb 4-4: new high speed USB device using ehci_hcd and address 24
[10968.180856] usb 4-4: new high speed USB device using ehci_hcd and address 29
[10969.574177] usb 4-4: new high speed USB device using ehci_hcd and address 40
[10970.376981] usb 4-4: new high speed USB device using ehci_hcd and address 47
[10971.009316] usb 4-4: new high speed USB device using ehci_hcd and address 51
[10971.689266] usb 4-4: new high speed USB device using ehci_hcd and address 56
[10972.124880] usb 4-4: new high speed USB device using ehci_hcd and address 59
[10972.940490] usb 4-4: new high speed USB device using ehci_hcd and address 65
[10973.981045] usb 4-4: new high speed USB device using ehci_hcd and address 74
[10974.260761] usb 4-4: new high speed USB device using ehci_hcd and address 76
chris@chris-laptop:~$

---

### Post by Cjmkee on 2008-09-26
sudo fdisk -l

chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b939b93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
chris@chris-laptop:~$

---

### Post by Cjmkee on 2008-09-26
What does that tell me? It looks like it recognizes that there is something in the USB port atleast. 

Where should I go from here?

---

### Post by DeeZiD on 2008-09-29
I have exactly the same problem.
There seems to be a problem with the FullSpeed USB2.0 driver.

You can temporarily disable this driver```
sudo rmmod ehci_hcd
```


Dennis

---

