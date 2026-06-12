---
title: "sd media not mounting"
date: 2010-07-12
forum: Hardware
---

### Post by jamesln5392 on 2010-07-12
I"m using the ubuntu netbook version of 10.04 on my acer aspire one d260.

The issue i have is when i insert a sd media card into my built in reader the card won't mount. And it's not visable anywhere not in disk utility or using the mount command. 


If i put in the card and run lsusb in console it sees the device...

> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0cf2:6250 ENE Technology, Inc. 
Looking in my system logs i see....
> 
Jul 12 16:44:04 james-netbook kernel: [ 1053.636097] usb 1-5: new high speed USB device using ehci_hcd and address 4
Jul 12 16:44:04 james-netbook kernel: [ 1053.770743] usb 1-5: configuration #1 chosen from 1 choice
To get a better understanding of what should happen, i watched the logs when i plugged in my thumb drive 

> 
Jul 12 09:12:54 james-netbook kernel: [  739.896094] usb 1-2: new high speed USB device using ehci_hcd and address 5
Jul 12 09:12:54 james-netbook kernel: [  740.032618] usb 1-2: configuration #1 chosen from 1 choice
Jul 12 09:12:54 james-netbook kernel: [  740.033246] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 12 09:12:54 james-netbook kernel: [  740.033636] usb-storage: device found at 5
Jul 12 09:12:54 james-netbook kernel: [  740.033647] usb-storage: waiting for device to settle before scanning
Jul 12 09:12:59 james-netbook kernel: [  745.032432] usb-storage: device scan complete
Jul 12 09:12:59 james-netbook kernel: [  745.033865] scsi 5:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
Jul 12 09:12:59 james-netbook kernel: [  745.044408] sd 5:0:0:0: [sdb] 506880 512-byte logical blocks: (259 MB/247 MiB)
Jul 12 09:12:59 james-netbook kernel: [  745.045307] sd 5:0:0:0: Attached scsi generic sg1 type 0
Jul 12 09:12:59 james-netbook kernel: [  745.045467] sd 5:0:0:0: [sdb] Write Protect is off
Jul 12 09:12:59 james-netbook kernel: [  745.045483] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jul 12 09:12:59 james-netbook kernel: [  745.045496] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul 12 09:12:59 james-netbook kernel: [  745.052687] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul 12 09:12:59 james-netbook kernel: [  745.052706]  sdb: sdb1
Jul 12 09:12:59 james-netbook kernel: [  745.135061] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul 12 09:12:59 james-netbook kernel: [  745.135083] sd 5:0:0:0: [sdb] Attached SCSI removable disk
I think it's a configuration issue, something isn't starting up......

Am i in the right train of thought? And does anyone have an idea how to fix this?

---

### Post by IcarusR on 2010-07-13
To help us help you & identify your card reader post output of 

```
lspci
```

Inbuilt card readers, in my experience, are usually on the pci bus not usb so I do not think any of the code you posted is relevant.

---

### Post by jamesln5392 on 2010-07-13
Here is the ouput  of lspci....But when i run lsusb it shows the card reader....

> 
james@james-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)




I did find a post in the bug section of Ubuntu that talks about the very same issue i am having,

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571402](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571402)

---

### Post by AltomineUK on 2010-07-14
Is this bug specifc to the netbook remix?.....i'm running Desktop edition on my netbook and I haven't come across this before....

---

### Post by IcarusR on 2010-07-14
> when i run lsusb it shows the card reader

Sorry my error, was expecting it to be on pci bus as I explained.

Reading the bug thread it would seem that you are far from alone in this issue.
I guess this hardware is not 'known' by the kernel & so no modules are being loaded for it.

---

### Post by avacado on 2010-10-14
I have reported the bug for my acer aspire d260

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)
the card reader does not work YET

please subscribe to the bug and add numbers who are waiting for this driver.
In the mean time buy a linux card reader external or use your camera as an ext drive.

---

