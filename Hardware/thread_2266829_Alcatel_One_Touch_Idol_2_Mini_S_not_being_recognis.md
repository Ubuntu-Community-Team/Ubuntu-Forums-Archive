---
title: "Alcatel One Touch Idol 2 Mini S not being recognised properly (not picking up card)"
date: 2015-02-25
forum: Hardware
---

### Post by Sslaxx on 2015-02-25
So, I have a brand-new Alcatel One Touch Idol 2 Mini S (mouthful of a name), and it has a 32GB MicroSD card with it.

I cannot get the phone to connect to Ubuntu (14.10; 3.16.0-31-generic).

[quote=dmesg][ 6249.134624] usb 1-3.3.2: new high-speed USB device number 12 using ehci-pci
[ 6249.227735] usb 1-3.3.2: New USB device found, idVendor=1bbb, idProduct=f000
[ 6249.227738] usb 1-3.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6249.227740] usb 1-3.3.2: Product: Android
[ 6249.227741] usb 1-3.3.2: Manufacturer: Android
[ 6249.227743] usb 1-3.3.2: SerialNumber: UBJC37BIRLX4MG2
[ 6249.228399] usb-storage 1-3.3.2:1.0: USB Mass Storage device detected
[ 6249.228496] scsi12 : usb-storage 1-3.3.2:1.0
[ 6250.228714] scsi 12:0:0:0: Direct-Access     Linux    File-CD Gadget   0000 PQ: 0 ANSI: 2
[ 6250.229171] scsi 12:0:0:1: CD-ROM            Linux    File-CD Gadget   0000 PQ: 0 ANSI: 2
[ 6250.231912] sd 12:0:0:0: Attached scsi generic sg7 type 0
[ 6250.236543] sd 12:0:0:0: [sdg] Attached SCSI removable disk
[ 6250.237546] sr1: scsi-1 drive
[ 6250.237683] sr 12:0:0:1: Attached scsi CD-ROM sr1
[ 6250.237820] sr 12:0:0:1: Attached scsi generic sg8 type 5
[ 6250.269716] systemd-udevd[4530]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 6250.269726] systemd-udevd[4530]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 6250.275766] systemd-udevd[4529]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 6250.275773] systemd-udevd[4529]: Failed to apply ACL on /dev/sr1: No such file or directory[/quote]

I understand the ACL issue is due to modem detection issues (phone can act as a hotspot), and the CD-ROM thing is the in-built drivers installation partition. The SD card is not being detected at all.

Anyone with any idea why?

Thanks.

---

