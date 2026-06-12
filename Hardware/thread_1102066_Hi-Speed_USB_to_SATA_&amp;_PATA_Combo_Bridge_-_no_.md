---
title: "Hi-Speed USB to SATA &amp; PATA Combo Bridge - no disk"
date: 2009-03-21
forum: Hardware
---

### Post by camel1cz on 2009-03-21
Hi to all,

I have bought SATA/PATA to USB converter hoping to use bunch of my old hard drives.

When I connect it to my laptop, it's detected but I have only sgX device, no disk capable of mounting/partitioning/etc.

Can anyone help, please?

Here are some info:

```

# lsusb
Bus 007 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```

```

# dmesg
[ 8073.820185] usb 7-2: new high speed USB device using ehci_hcd and address 4
[ 8073.955347] usb 7-2: configuration #1 chosen from 1 choice
[ 8073.956967] scsi6 : SCSI emulation for USB Mass Storage devices
[ 8073.960524] usb-storage: device found at 4
[ 8073.960534] usb-storage: waiting for device to settle before scanning
[ 8078.956526] usb-storage: device scan complete
[ 8078.957403] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 8078.958915] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 8078.959111] sd 6:0:0:0: Attached scsi generic sg2 type 0


```

Thank you!

---

### Post by menonfire12 on 2009-05-21
> **camel1cz said:**
> Hi to all,

I have bought SATA/PATA to USB converter hoping to use bunch of my old hard drives.

When I connect it to my laptop, it's detected but I have only sgX device, no disk capable of mounting/partitioning/etc.

Can anyone help, please?

Here are some info:

```

# lsusb
Bus 007 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```

```

# dmesg
[ 8073.820185] usb 7-2: new high speed USB device using ehci_hcd and address 4
[ 8073.955347] usb 7-2: configuration #1 chosen from 1 choice
[ 8073.956967] scsi6 : SCSI emulation for USB Mass Storage devices
[ 8073.960524] usb-storage: device found at 4
[ 8073.960534] usb-storage: waiting for device to settle before scanning
[ 8078.956526] usb-storage: device scan complete
[ 8078.957403] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 8078.958915] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 8078.959111] sd 6:0:0:0: Attached scsi generic sg2 type 0


```

Thank you!


I Have exactly the same problem as yours.

```

# lsusb
Bus 005 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```

```

# dmesg
[  727.824258] usb 5-7: new high speed USB device using ehci_hcd and address 3
[  727.957968] usb 5-7: configuration #1 chosen from 1 choice
[  728.184223] usbcore: registered new interface driver libusual
[  728.234549] Initializing USB Mass Storage driver...
[  728.250469] scsi4 : SCSI emulation for USB Mass Storage devices
[  728.252941] usbcore: registered new interface driver usb-storage
[  728.253386] USB Mass Storage support registered.
[  728.253923] usb-storage: device found at 3
[  728.253931] usb-storage: waiting for device to settle before scanning
[  733.250058] usb-storage: device scan complete
[  733.251044] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  733.262018] sd 4:0:0:0: [sdb] Attached SCSI disk
[  733.262093] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

There is nothing wrong with the enclosure because it works in Windows XP.

Let me know it you got it working or any body to help, thanks!.

---

### Post by camel1cz on 2009-05-21
Hi,

I actually got it working.

The device and/or kernel driver seems to be sensitive to the way how you connect all the parts together. I mean the order.

I *THINK* correct way is as follows but I cannot test it as I don't have the device by hand.

1) plug the power into the hard drive
2) wait for the drive to spin up
3) plug the convertor into the hard drive
4) plug the USB cord into your computer

Next thing to try is 3 - 1 - 2 - 4
Can do more testing tommorow but you should be able to find out by yourself easily.

Hope it'll help.

---

### Post by superc0w on 2011-01-04
This is the most ridiculous thing on the planet, but yes ORDER DOES MATTER!  

1) plug the power into the hard drive
2) wait for the drive to spin up
3) plug the convertor into the hard drive
4) plug the USB cord into your computer

---

