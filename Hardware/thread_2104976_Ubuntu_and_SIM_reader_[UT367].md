---
title: "Ubuntu and SIM reader [UT367]"
date: 2013-01-14
forum: Hardware
---

### Post by e-San on 2013-01-14
Hi!

I bought multi-reader USB device, with SIM support.
I checked it out on Windows and works wuite fine.

I prefer to use linux any time it is possible, so i am looking for solution to read SIM with linux.

First of all! I do not ask for software - sooner or later, maybe.
I am looking for information how to at last ENABLE SIM reader.

Some information:
- It is built on UT367 all-in-one chip.
- It has MS, MS2 and few more cards support.
- It works as mass storage.

About the chip: [http://www.ite.com.tw/TW/products_more.aspx?CategoryID=4&ID=14,57](http://www.ite.com.tw/TW/products_more.aspx?CategoryID=4&ID=14,57)

My dmesg:
```
[11116.748072] usb 1-3: >new high-speed USB device number 16 using ehci_hcd
[11116.880471] usb 1-3: >config 1 interface 1 altsetting 0 bulk endpoint 0x5 has invalid maxpacket 16
[11116.880483] usb 1-3: >config 1 interface 1 altsetting 0 bulk endpoint 0x86 has invalid maxpacket 16
[11117.029348] usb 1-3: >New USB device found, idVendor=1307, idProduct=0368
[11117.029359] usb 1-3: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11117.029366] usb 1-3: >Product: MultiCard Device
[11117.029372] usb 1-3: >Manufacturer: Generic   
[11117.029378] usb 1-3: >SerialNumber: 00000000000006
[11117.031460] scsi14 : usb-storage 1-3:1.0
[11118.029025] scsi 14:0:0:0: >Direct-Access     Generic  SD/MMC           0.00 PQ: 0 ANSI: 2
[11118.030162] scsi 14:0:0:1: >Direct-Access     Generic  microSD          0.00 PQ: 0 ANSI: 2
[11118.030752] scsi 14:0:0:2: >Direct-Access     Generic  MS/MS-PRO        0.00 PQ: 0 ANSI: 2
[11118.039890] sd 14:0:0:0: >Attached scsi generic sg2 type 0
[11118.041621] sd 14:0:0:1: >Attached scsi generic sg3 type 0
[11118.041864] sd 14:0:0:0: >[sdc] Attached SCSI removable disk
[11118.042243] sd 14:0:0:2: >Attached scsi generic sg4 type 0
[11118.047003] sd 14:0:0:2: >[sde] Attached SCSI removable disk
[11118.047625] sd 14:0:0:1: >[sdd] Attached SCSI removable disk
```

lsusb:
```
Bus 001 Device 016: ID 1307:0368 Transcend Information, Inc. 
```

diff /dev:
```
san@azazel:/dev/shm$ diff 1 2
79a80,82
> sdc
> sdd
> sde
81a85,87
> sg2
> sg3
> sg4

```

Interested at anything more? Any hope?

Regards!

---

### Post by Whoopie on 2013-01-15
It's just a guess, but your SIM reader could be available via PC/SC. You could install the pcsc-tools package and check if your reader is found via "pcsc_scan".

---

### Post by e-San on 2013-01-15
```
san@azazel:~/Pobrane/Harmony300i$ pcscd
san@azazel:~/Pobrane/Harmony300i$ sudo pcscd
[sudo] password for san: 
san@azazel:~/Pobrane/Harmony300i$ pcsc_scan 
PC/SC device scanner
V 1.4.20 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.3
Using reader plug'n play mechanism
Scanning present readers...
Waiting for the first reader...^C
san@azazel:~/Pobrane/Harmony300i$ sudo pcsc_scan 
PC/SC device scanner
V 1.4.20 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.3
Using reader plug'n play mechanism
Scanning present readers...
Waiting for the first reader...
```

Belive there is no hope for me. It does not change since quite few minutes...

---

### Post by ut0ugh1 on 2013-05-25
I bought the same Eminent compact reader (mine has revision 4 same id, yours?). as you can see ```


[11116.880471] usb 1-3: >config 1 interface 1 altsetting 0 bulk endpoint 0x5 has invalid maxpacket 16 [11116.880483] usb 1-3: >config 1 interface 1 altsetting 0 bulk endpoint 0x86 has invalid maxpacket 16
```
there are different endpoint that means that there is a way to switch to sim reader probably through usbmodeswitch (but i was not able to do that) which id shoud be 0367 as in the inf windows file.
First i have tried to modify  /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Info.plist inserting this ```
108d107
<         <string>0x1307</string>
303d301
<         <string>0x0368</string>
498d495
<         <string>Eminent Compact Card Reader USB 2.0 EM1060 rev 4</string>


``` but it did not work at all.

---

