---
title: "Automounting USB doesn't always work"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Pconfig on 2007-12-04
Hey,

First of all, i know there are some threads going on about issues with automounting usb devices but i have a feeling that my problem is different. I have a HP Pavilion dv6500 laptop and got ubuntu finally to work. The system kept hanging at loading the bluetooth module. To get passed this issue i had to disable bluetooth from booting (so bluetooth doesn't work at all), just telling this because it might have something to do with this issue.

Now the problem is when i insert a USB stick after the computer is booted, nothing happens. However, when i boot the pc with a USB device attached to it, it start recognizing every new USB device i add later on after the pc got booted.

So boot up with a stick in it ==> No problems
Boot up without a usb device ==> Nothing gets recognized

dmesg gave me the following outputs

With stick booted:
```
[   80.706749] usb 7-1: USB disconnect, address 2
[   81.728111] usb 7-1: new high speed USB device using ehci_hcd and address 6
[   81.753617] usb 7-1: configuration #1 chosen from 1 choice
[   81.754001] scsi6 : SCSI emulation for USB Mass Storage devices
[   81.754093] usb-storage: device found at 6
[   81.754098] usb-storage: waiting for device to settle before scanning
[   82.427182] usb-storage: device scan complete
[   82.427603] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2
[   82.430259] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[   82.431003] sd 6:0:0:0: [sdb] Write Protect is off
[   82.431010] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   82.431015] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   82.433593] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[   82.434251] sd 6:0:0:0: [sdb] Write Protect is off
[   82.434257] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   82.434261] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   82.434267]  sdb: sdb1
[   82.435242] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   82.435311] sd 6:0:0:0: Attached scsi generic sg2 type 0
```

USB not mounted

```
[   80.320682] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   80.330088] usb 2-2: configuration #1 chosen from 1 choice
[   82.554039] usb 7-1: new high speed USB device using ehci_hcd and address 5
[   82.580033] usb 7-1: configuration #1 chosen from 1 choice
```

As you can see i already tried to disable EHCI but that didn't help. I also tried to boot with the paramaters 

```
noapic irqpoll noirqdebug
```

No luck either..

Anyone has any ideas?

Thanks
Thomas

---

### Post by Elsa on 2007-12-05
I am new to any Linux system but I just installed Xubuntu in my old eMachines three weeks or so ago. I also wanted to use a USB stick. The very first time I plugged it in to the port (USB 1.1) the machine recognized it although it took 30 minutes until I could see the content of the USB stick. I received "Cannot Unmount Volume" error message, though.

Then I tried booting the machine with the USB stick at the port. The drive showed up on the desktop but when I tried to mount or open, it just disappeared. When I booted the machine without the USB stick nothing showed up on the desktop.

---

