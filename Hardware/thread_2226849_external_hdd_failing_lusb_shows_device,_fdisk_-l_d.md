---
title: "external hdd failing? lusb shows device, fdisk -l does not"
date: 2014-05-29
forum: Hardware
---

### Post by paulbrodersen on 2014-05-29
Thank for you taking the time looking at this thread.

I have problems mounting an external hard drive (Western Digital, 1TB) that I have used for the past two or three years without any problems, including this morning. I have not updated the OS in the past week so I can exclude driver issues. This might be coincidental, but the problem first occurred after I started up my laptop without disconnecting the device. Since I have set my boot order such that usb devices are given top priority, I presume that it tried to boot from the drive; since there is no OS installed on there it failed to do anything productive and I did a hard reboot, this time disconnecting the device. 

Now, the drive spins up and I can detect it with lsusb, however, fdisk -l and blkid only show my internal partitions. The relevant output from dmesg below:

```
[ 1192.244431] usb 1-1.2: new high-speed USB device number 5 using ehci-pci
[ 1192.986331] usb 1-1.2: New USB device found, idVendor=1058, idProduct=0000
[ 1192.986341] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1192.986347] usb 1-1.2: Product: BAD PCB
[ 1192.986351] usb 1-1.2: Manufacturer: WD
[ 1192.986356] usb 1-1.2: SerialNumber: 10B870BE10B871E6
[ 1193.054771] Initializing USB Mass Storage driver...
[ 1193.054868] scsi6 : usb-storage 1-1.2:1.0
[ 1193.054933] usbcore: registered new interface driver usb-storage
[ 1193.054935] USB Mass Storage support registered.
[ 1194.052850] scsi 6:0:0:0: Direct-Access     WD       BAD PCB          0000 PQ: 0 ANSI: 6
[ 1194.053776] scsi 6:0:0:1: Enclosure         WD       Ses              0000 PQ: 0 ANSI: 6
[ 1194.054631] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1194.055441] sd 6:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[ 1194.056137] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[ 1224.863858] usb 1-1.2: reset high-speed USB device number 5 using ehci-pci
[ 1239.898869] usb 1-1.2: device descriptor read/64, error -110
[ 1255.037389] usb 1-1.2: device descriptor read/64, error -110
[ 1255.213096] usb 1-1.2: reset high-speed USB device number 5 using ehci-pci
[ 1270.248095] usb 1-1.2: device descriptor read/64, error -110
[ 1285.387431] usb 1-1.2: device descriptor read/64, error -110
[ 1285.562240] usb 1-1.2: reset high-speed USB device number 5 using ehci-pci
[ 1295.944487] usb 1-1.2: device not accepting address 5, error -110
[ 1296.016514] usb 1-1.2: reset high-speed USB device number 5 using ehci-pci
[ 1306.398647] usb 1-1.2: device not accepting address 5, error -110
[ 1306.398934] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 1306.398955] sd 6:0:0:0: rejecting I/O to offline device
[ 1306.398962] sd 6:0:0:0: rejecting I/O to offline device
[ 1306.398965] sd 6:0:0:0: [sdb] READ CAPACITY(16) failed
[ 1306.398966] sd 6:0:0:0: [sdb]  
[ 1306.398967] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1306.398968] sd 6:0:0:0: [sdb] Sense not available.
[ 1306.398970] sd 6:0:0:0: [sdb] Using 0xffffffff as device size
[ 1306.398971] sd 6:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 1306.398974] sd 6:0:0:0: [sdb] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
[ 1306.398975] sd 6:0:0:0: [sdb] 0-byte physical blocks
[ 1306.398978] sd 6:0:0:0: rejecting I/O to offline device
[ 1306.398981] sd 6:0:0:0: [sdb] Write Protect is off
[ 1306.398982] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1306.398984] sd 6:0:0:0: rejecting I/O to offline device
[ 1306.398986] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1306.398987] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1306.399013] usb 1-1.2: USB disconnect, device number 5
[ 1306.399123] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 1306.399126] sd 6:0:0:0: [sdb]  
[ 1306.399127] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1306.399128] sd 6:0:0:0: [sdb] Sense not available.
[ 1306.399139] sd 6:0:0:0: [sdb] Write Protect is on
[ 1306.399141] sd 6:0:0:0: [sdb] Mode Sense: 00 30 ab f6
[ 1306.399149] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1306.399151] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1306.399154] sdb: detected capacity change from 2199023255552 to 0
[ 1306.399225] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 1306.399227] sd 6:0:0:0: [sdb]  
[ 1306.399228] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1306.399230] sd 6:0:0:0: [sdb] Sense not available.
[ 1306.399249] sd 6:0:0:0: [sdb] Write Protect is off
[ 1306.399251] sd 6:0:0:0: [sdb] Mode Sense: 00 90 48 1d
[ 1306.399259] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1306.399261] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1306.399262] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 1306.406702] scsi 6:0:0:1: Failed to get diagnostic page 0x10000
[ 1306.406713] scsi 6:0:0:1: Failed to bind enclosure -19
[ 1306.406756] ses 6:0:0:1: Attached Enclosure device
[ 1306.478598] usb 1-1.2: new high-speed USB device number 6 using ehci-pci
[ 1321.513560] usb 1-1.2: device descriptor read/64, error -110
[ 1336.652450] usb 1-1.2: device descriptor read/64, error -110
[ 1336.828073] usb 1-1.2: new high-speed USB device number 7 using ehci-pci
[ 1351.862776] usb 1-1.2: device descriptor read/64, error -110
[ 1367.001514] usb 1-1.2: device descriptor read/64, error -110
[ 1367.177108] usb 1-1.2: new high-speed USB device number 8 using ehci-pci
[ 1377.559333] usb 1-1.2: device not accepting address 8, error -110
[ 1377.631399] usb 1-1.2: new high-speed USB device number 9 using ehci-pci
[ 1388.013462] usb 1-1.2: device not accepting address 9, error -110
[ 1388.013725] hub 1-1:1.0: unable to enumerate USB device on port 2
[ 1421.311669] usb 1-1.2: new high-speed USB device number 10 using ehci-pci
[ 1422.053130] usb 1-1.2: New USB device found, idVendor=1058, idProduct=0000
[ 1422.053140] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1422.053146] usb 1-1.2: Product: BAD PCB
[ 1422.053151] usb 1-1.2: Manufacturer: WD
[ 1422.053155] usb 1-1.2: SerialNumber: 10B865C410B866E6
[ 1422.053877] scsi7 : usb-storage 1-1.2:1.0
[ 1423.052451] scsi 7:0:0:0: Direct-Access     WD       BAD PCB          0000 PQ: 0 ANSI: 6
[ 1423.053434] scsi 7:0:0:1: Enclosure         WD       Ses              0000 PQ: 0 ANSI: 6
[ 1423.054939] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1423.055172] ses 7:0:0:1: Attached Enclosure device
[ 1423.055317] ses 7:0:0:1: Attached scsi generic sg3 type 13
[ 1423.057797] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[ 1453.324600] usb 1-1.2: reset high-speed USB device number 10 using ehci-pci
[ 1468.359546] usb 1-1.2: device descriptor read/64, error -110
[ 1483.498200] usb 1-1.2: device descriptor read/64, error -110
[ 1483.674004] usb 1-1.2: reset high-speed USB device number 10 using ehci-pci
[ 1498.708798] usb 1-1.2: device descriptor read/64, error -110
[ 1513.847686] usb 1-1.2: device descriptor read/64, error -110
[ 1514.023039] usb 1-1.2: reset high-speed USB device number 10 using ehci-pci
[ 1524.405192] usb 1-1.2: device not accepting address 10, error -110
[ 1524.477263] usb 1-1.2: reset high-speed USB device number 10 using ehci-pci
[ 1534.859424] usb 1-1.2: device not accepting address 10, error -110
[ 1534.859794] sd 7:0:0:0: Device offlined - not ready after error recovery
[ 1534.859816] sd 7:0:0:0: rejecting I/O to offline device
[ 1534.859824] sd 7:0:0:0: rejecting I/O to offline device
[ 1534.859827] sd 7:0:0:0: [sdb] READ CAPACITY(16) failed
[ 1534.859829] sd 7:0:0:0: [sdb]  
[ 1534.859830] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1534.859831] sd 7:0:0:0: [sdb] Sense not available.
[ 1534.859832] sd 7:0:0:0: [sdb] Using 0xffffffff as device size
[ 1534.859833] sd 7:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 1534.859836] sd 7:0:0:0: [sdb] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
[ 1534.859837] sd 7:0:0:0: [sdb] 0-byte physical blocks
[ 1534.859841] sd 7:0:0:0: rejecting I/O to offline device
[ 1534.859843] sd 7:0:0:0: [sdb] Write Protect is off
[ 1534.859844] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1534.859846] sd 7:0:0:0: rejecting I/O to offline device
[ 1534.859848] sd 7:0:0:0: [sdb] Asking for cache data failed
[ 1534.859849] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1534.859875] usb 1-1.2: USB disconnect, device number 10
[ 1534.859959] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 1534.867411] ses 7:0:0:1: Failed to get diagnostic page 0x10000
[ 1534.867417] ses 7:0:0:1: Failed to bind enclosure -19
[ 1534.939463] usb 1-1.2: new high-speed USB device number 11 using ehci-pci
[ 1549.974288] usb 1-1.2: device descriptor read/64, error -110
[ 1565.113189] usb 1-1.2: device descriptor read/64, error -110
[ 1565.288535] usb 1-1.2: new high-speed USB device number 12 using ehci-pci
[ 1580.323473] usb 1-1.2: device descriptor read/64, error -110
[ 1595.462240] usb 1-1.2: device descriptor read/64, error -110
[ 1595.637842] usb 1-1.2: new high-speed USB device number 13 using ehci-pci
[ 1606.020115] usb 1-1.2: device not accepting address 13, error -110
[ 1606.092128] usb 1-1.2: new high-speed USB device number 14 using ehci-pci
[ 1616.474410] usb 1-1.2: device not accepting address 14, error -110
[ 1616.474714] hub 1-1:1.0: unable to enumerate USB device on port 2
```

In my desperation, I also tried to mount the hdd under windows but to no avail (it sees that a disk is connected and tries to install drivers - which should already be installed since I have used the disk under windows before - before giving an error message that the drive could not be installed; ominently, the device is then listed as 'Bad PCB' in the usb connected devices menu in the startup bar).

I have backups of many albeit not all files on the drive. In particular, I would loose several weeks of work if I cannot recover the data on there. Hence any suggestions whatsoever would be welcome.

---

### Post by sudodus on 2014-05-29
Welcome to the Ubuntu Forums :-)

If you cannot see the drive with

```
fdisk -l
```

 try

```
sudo fdisk -lu
```

 try also ```
sudo parted -l
```

If still no go, there might be problems with the connection to the drive. If it is in a box, the problem might be the electronics in the box (so that the disk unit inside might be OK). There might also be problems with the USB port in the computer. Try other ports and other computers.

---

### Post by paulbrodersen on 2014-05-29
Thank you for your recommendations.

I have tried mounting it on 2 other computers (Lubuntu, Windows 7) to no avail. Other ports on the same laptop unsurprisingly did not give any better results. The USB cable is not the problem, either (I successfully connected a different device with the same cable). None of the commands above detected the external hdd. 
 
I concur that it most likely is a hardware issue; however, I was hoping that somebody would have a more precise diagnosis of the problem. In particular, I was hoping that somebody could conclude from the dmesg output whether the problem is with the connector/SATA port, or whether the PCB is dying. The former would not be much of a problem but to my layman's eyes seems unlikely since lsusb still recognizes the device. Replacing a faulty PCB apparently is a more delicate and risky operation, although I do happen to have another external of the same type so swapping the PCBs would definitely be in the realm of the possible.

---

### Post by sudodus on 2014-05-30
Are you talking about the printed circuit board of the HDD itself or of that of the external box?

If the HDD is built into (was delivered with) an external box, it might be possible to break it open and take out the HDD. I colleague of mine did that some years ago. The HDD and  the printed circuit board of the HDD itself were OK, so it could be used as a standard SATA disk.

---

### Post by paulbrodersen on 2014-06-01
It wasn't the connector to the SATA port (which in my WD HDD was not actually a standard SATA port so I tried the connector from my second HDD (same model)).
Just before I embarked on exchanging the circuit boards, I thought I would try the good ole banging-against-the-desk method, and that did in fact work - God knows why. Data recovered, me happy.

Thanks for your time.

---

### Post by sudodus on 2014-06-01
I'm glad the good ole banging-against-the-desk method worked for you :-D

But I would not rely on this disk. Who knows if it will work next time? You can certainly use it for testing purposes, for example to test new linux distros and versions, but do not store important data on on this disk.

---

