---
title: "USB Stick failure"
date: 2018-10-09
forum: Hardware
---

### Post by dameffy on 2018-10-09
Hello!

I'having an issue with an USB stick that seems to be corrupt [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/frown.gif[/IMG].  When pluggin it it it takes a while until it is recognised (I've  already disabled the ehci_pci driver as suggested somewhere...). To make  it short here is the output from dmesg after inserting the stick:
```
[ 1719.504232] usb 4-2: USB disconnect, device number 6
[ 1722.748986] usb 4-2: new full-speed USB device number 7 using ohci-pci
[ 1728.105510] usb 4-2: unable to read config index 0 descriptor/all
[ 1728.105525] usb 4-2: can't read configurations, error -110
[ 1728.253190] usb 4-2: new full-speed USB device number 8 using ohci-pci
[ 1736.421473] usb 4-2: device not accepting address 8, error -32
[ 1736.421553] usb usb4-port2: attempt power cycle
[ 1736.885492] usb 4-2: new full-speed USB device number 9 using ohci-pci
[ 1737.115250] usb 4-2: New USB device found, idVendor=1f75, idProduct=0917
[ 1737.115260] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1737.115264] usb 4-2: Product: PenDrive
[ 1737.115268] usb 4-2: Manufacturer: Innostor
[ 1737.115272] usb 4-2: SerialNumber: 000000000000000487
[ 1737.117364] usb-storage 4-2:1.0: USB Mass Storage device detected
[ 1737.118733] scsi host6: usb-storage 4-2:1.0
[ 1739.540526] scsi 6:0:0:0: Direct-Access     Innostor Innostor         1.00 PQ: 0 ANSI: 6
[ 1739.541848] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1739.550463] sd 6:0:0:0: [sdb] 61740154 512-byte logical blocks: (31.6 GB/29.4 GiB)
[ 1739.556444] sd 6:0:0:0: [sdb] Write Protect is on
[ 1739.556448] sd 6:0:0:0: [sdb] Mode Sense: 23 00 80 00
[ 1739.562456] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[ 1739.622523]  sdb: sdb1
[ 1739.652471] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```
So far so good (more or less). Problem is that the file system is defect, so I tried to make an image with dd:
```
dd if=/dev/sdb1 of=/home/user/img.iso conv=noerror,sync status=progress
```
After a short while (~60MB) dd stops; dmesg gives me
```
[ 2053.139410] usb 4-2: reset full-speed USB device number 9 using ohci-pci
```
dd's output is now I/O error and dmesg tells me
```
...
[ 2125.308100] sd 6:0:0:0: rejecting I/O to offline device
[ 2125.308107] sd 6:0:0:0: rejecting I/O to offline device
[ 2125.308182] sd 6:0:0:0: rejecting I/O to offline device
[ 2125.308190] sd 6:0:0:0: rejecting I/O to offline device
[ 2125.308197] sd 6:0:0:0: rejecting I/O to offline device
[ 2125.308204] sd 6:0:0:0: rejecting I/O to offline device
...
```
So connection somehow gets lost [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/frown.gif[/IMG]. I tried several USB ports on my machine, but result is always the same...
Any suggestions how to rescue the data?

---

### Post by westie457 on 2018-10-09
What file system is on the usb stick (NTFS, FAT, Ext4 as examples)?

Maybe this will give you some ideas to fix. [https://askubuntu.com/questions/968951/usb-turned-into-read-only-file-how-to-make-it-writable](https://askubuntu.com/questions/968951/usb-turned-into-read-only-file-how-to-make-it-writable)

---

