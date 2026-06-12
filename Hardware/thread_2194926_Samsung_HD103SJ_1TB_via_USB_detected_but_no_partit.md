---
title: "Samsung HD103SJ 1TB via USB detected but no partition found"
date: 2013-12-21
forum: Hardware
---

### Post by bbmiojo on 2013-12-21
Hi all,

After 2 years, finally the a*** of the video guy of my marriage sent a HD with the raw videos. But I need your help on connecting the HD to extract the content and then send to an editor, so my wife can finally watch the recording. I can't say how important this is to her, but I'm sure you guys can imagine as I can too. :-)

I have a Samsung HD103SJ 1TB and I'm using a USB3/SATA Bridge adapter cable to plug it to my laptop. The device is recognized, but no partition is found. It works fine though on Windows. Here's the log:

```
# dmesg
[  987.568240] usb 2-4: new high-speed USB device number 6 using ehci-pci
[  987.704887] usb 2-4: New USB device found, idVendor=05e3, idProduct=0731
[  987.704900] usb 2-4: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[  987.704908] usb 2-4: Product: USB to S-ATA
[  987.704915] usb 2-4: Manufacturer: Genesyslogic
[  987.704921] usb 2-4: SerialNumber: 00000000000025432
[  987.706682] usb-storage 2-4:1.0: USB Mass Storage device detected
[  987.707357] scsi10 : usb-storage 2-4:1.0
[  988.705572] scsi 10:0:0:0: Direct-Access     Generic  USB3/SATA Bridge 9094 PQ: 0 ANSI: 0
[  988.706249] sd 10:0:0:0: Attached scsi generic sg2 type 0
[  988.714126] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  988.715254] sd 10:0:0:0: [sdb] Asking for cache data failed
[  988.715265] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  988.722979] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  988.723995] sd 10:0:0:0: [sdb] Asking for cache data failed
[  988.723999] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  988.725356] sd 10:0:0:0: [sdb] Attached SCSI disk

```

Again, no partition found (for example: /dev/sdb1). Here's the lsscsi output:

```
# lsscsi
[0:0:0:0]    disk    ATA      INTEL SSDSA2CW12 4PC1  /dev/sda 
[1:0:0:0]    cd/dvd  TSSTcorp DVD+-RW TS-U633A D300  /dev/sr0 
[10:0:0:0]   disk    Generic  USB3/SATA Bridge 9094  /dev/sdb 
```

Finally, the /proc/scsi/scsi output:

```
# cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: INTEL SSDSA2CW12 Rev: 4PC1
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: DVD+-RW TS-U633A Rev: D300
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi10 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB3/SATA Bridge Rev: 9094
  Type:   Direct-Access                    ANSI  SCSI revision: 00
```

The cable I'm using is this one: [IMG]http://img.alibaba.com/img/pb/456/680/882/882680456_657.jpg[/IMG]

Anyone has any good idea to try out?

Thanks!

---

### Post by PaulBx on 2013-12-22
It's your wedding, dude, don't fool around. If it works in Windows, then use Windows.

---

### Post by bbmiojo on 2013-12-22
Yeah man, but I don't have Windows.

Although I think this is a power issue. As the HD is a 3,5', big as hell, I don't think the USB port for power is providing enough gas. Will probably have to get a deck or a esata/sata cable.

---

### Post by efflandt on 2013-12-22
How do you know that it works in Windows if you do not have Windows, and wherever it does, is it with that dongle? BizLink shows a picture of that "USB 3.0 to SATA 6 Gbps Dongle", but Description, Specifications, etc. all say just NIL (ie, nothing):
[http://www.bizlinktech.com/industries/detail.aspx?Type=100&CId=4&Id=128&R=1](http://www.bizlinktech.com/industries/detail.aspx?Type=100&CId=4&Id=128&R=1)

 USB is only required to provide 5 VDC @ 500 mA (1 amp total for 2). Maybe you need a SATA caddy with its own power supply. especially if it is a desktop drive. The SATA caddy I have with USB or eSATA connections has a separate power supply that outputs both 12 VDC and 5 VDC @ 2 amps each (although, it is for 2 drives). When the Linux partition of my desktop 1 TB drive failed I used the caddy to image my Windows partitions to a new drive, then reinstalled Ubuntu and copied my old /home directory to it.

---

### Post by mastablasta on 2013-12-22
what kind of cabel is that? :-O
just use the normal usb to usb cable (usually they come with the disk) and it should work fine.

as for power if it's 3,5" it porbabyl uses external power supply. those usually also come with the disk.

i dont' know what exact model you disk is but i have large 2TB samsung drive with extra powersupply plugged in to RaspberryPi via USB and works well. i imagine other samsung drives are also compatible with linux.

---

