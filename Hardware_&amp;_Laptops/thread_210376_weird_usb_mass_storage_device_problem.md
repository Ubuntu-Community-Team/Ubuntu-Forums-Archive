---
title: "weird usb mass storage device problem"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by dumbsnake on 2006-07-06
So this is very wierd to me.  I plugged in my digital camera (FinePix A205) and ubuntu detected it.  The icon popped up on the desktop.  It asked me if I wanted to copy the pictures off the camera.  I said to ignore it.  I then went to open the icon.  I went through the directory tree and it worked and stuff, but then all of the sudden, it unmounted and now it is gone.  I tried unpluggin it and pluggin it in again, but now it won't come up.  Clearly it worked for a second because I even saw the previews of the pictures on the camera before it unmounted.  Any ideas?

---

### Post by christhemonkey on 2006-07-06
Can you post the output of dmesg?
```
dmesg 
```

---

### Post by dumbsnake on 2006-07-06
not sure where you wanted me to start... but here it is



[17619800.704000] Initializing USB Mass Storage driver...
[17619800.728000] usbcore: registered new driver usb-storage
[17619800.728000] USB Mass Storage support registered.
[17619803.360000] usb 4-2: new full speed USB device using uhci_hcd and address 4
[17619803.504000] scsi2 : SCSI emulation for USB Mass Storage devices
[17619803.504000] usb-storage: device found at 4
[17619803.504000] usb-storage: waiting for device to settle before scanning
[17619803.876000] usb 4-2: USB disconnect, address 4
[17619805.376000] usb 4-2: new full speed USB device using uhci_hcd and address 5
[17619805.520000] scsi3 : SCSI emulation for USB Mass Storage devices
[17619805.520000] usb-storage: device found at 5
[17619805.520000] usb-storage: waiting for device to settle before scanning
[17619810.524000]   Vendor: FUJIFILM  Model: USB-DRIVEUNIT     Rev: 1.00
[17619810.524000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17619810.532000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[17619810.540000] sdb: Write Protect is off
[17619810.540000] sdb: Mode Sense: 0b 00 00 08
[17619810.540000] sdb: assuming drive cache: write through
[17619810.560000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[17619810.564000] sdb: Write Protect is off
[17619810.564000] sdb: Mode Sense: 0b 00 00 08
[17619810.564000] sdb: assuming drive cache: write through
[17619810.564000]  sdb: sdb1
[17619810.588000] sd 3:0:0:0: Attached scsi removable disk sdb
[17619810.588000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[17619810.588000] usb-storage: device scan complete
[17619812.164000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17619839.012000] usb 4-2: USB disconnect, address 5
[17619839.012000] sd 3:0:0:0: SCSI error: return code = 0x10000
[17619839.012000] end_request: I/O error, dev sdb, sector 10624
[17619839.012000] Buffer I/O error on device sdb1, logical block 10575
[17619839.012000] sd 3:0:0:0: rejecting I/O to device being removed
[17619839.012000] Buffer I/O error on device sdb1, logical block 10576
[17619839.012000] Buffer I/O error on device sdb1, logical block 10577
[17619839.012000] Buffer I/O error on device sdb1, logical block 10578
[17619839.012000] Buffer I/O error on device sdb1, logical block 10579
[17619839.012000] Buffer I/O error on device sdb1, logical block 10580
[17619839.012000] Buffer I/O error on device sdb1, logical block 10581
[17619839.012000] Buffer I/O error on device sdb1, logical block 10582
[17619839.012000] Buffer I/O error on device sdb1, logical block 10583
[17619839.012000] Buffer I/O error on device sdb1, logical block 10584
[17619839.012000] sd 3:0:0:0: SCSI error: return code = 0x10000
[17619839.012000] end_request: I/O error, dev sdb, sector 10752
[17619839.012000] sd 3:0:0:0: rejecting I/O to device being removed
[17619839.012000] sd 3:0:0:0: rejecting I/O to device being removed
[17619839.012000] sd 3:0:0:0: rejecting I/O to device being removed
[17619839.020000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 175) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 176) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 177) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 178) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 179) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 180) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 181) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 182) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 183) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 184) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 185) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 186) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 187) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 188) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 189) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 190) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 191) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 192) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 193) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 194) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 195) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 196) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 197) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 198) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 199) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 200) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 201) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 202) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 203) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 204) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 205) failed
[17619839.108000]  3:0:0:0: rejecting I/O to dead device
[17619839.108000] FAT: Directory bread(block 206) failed
[17619839.688000]  3:0:0:0: rejecting I/O to dead device
[17619847.208000] usb 4-2: new full speed USB device using uhci_hcd and address 6
[17619847.352000] scsi4 : SCSI emulation for USB Mass Storage devices
[17619847.352000] usb-storage: device found at 6
[17619847.352000] usb-storage: waiting for device to settle before scanning
[17619852.468000] usb 4-2: reset full speed USB device using uhci_hcd and address 6
[17619852.600000] usb 4-2: device descriptor read/all, error -71
[17619852.768000] usb 4-2: USB disconnect, address 6
[17619852.768000] usb-storage: device scan complete
[17619853.508000] usb 4-2: new full speed USB device using uhci_hcd and address 7
[17619853.656000] scsi5 : SCSI emulation for USB Mass Storage devices
[17619853.656000] usb-storage: device found at 7
[17619853.656000] usb-storage: waiting for device to settle before scanning
[17619865.268000] usb 4-2: reset full speed USB device using uhci_hcd and address 7
[17619868.380000] usb 4-2: device descriptor read/64, error -110
[17619883.596000] usb 4-2: device descriptor read/64, error -110
[17619883.812000] usb 4-2: reset full speed USB device using uhci_hcd and address 7
[17619886.924000] usb 4-2: device descriptor read/64, error -110
[17619902.140000] usb 4-2: device descriptor read/64, error -110
[17619902.356000] usb 4-2: reset full speed USB device using uhci_hcd and address 7
[17619912.764000] usb 4-2: device not accepting address 7, error -110
[17619912.876000] usb 4-2: reset full speed USB device using uhci_hcd and address 7
[17619923.284000] usb 4-2: device not accepting address 7, error -110
[17619923.284000] usb 4-2: USB disconnect, address 7
[17619923.284000]  5:0:0:0: scsi: Device offlined - not ready after error recovery
[17619923.296000] usb-storage: device scan complete
[17619923.408000] usb 4-2: new full speed USB device using uhci_hcd and address 8
[17619926.520000] usb 4-2: device descriptor read/64, error -110
[17619941.736000] usb 4-2: device descriptor read/64, error -110
[17619941.952000] usb 4-2: new full speed USB device using uhci_hcd and address 9
[17619945.064000] usb 4-2: device descriptor read/64, error -110
[17619960.280000] usb 4-2: device descriptor read/64, error -110
[17619960.496000] usb 4-2: new full speed USB device using uhci_hcd and address 10
[17619970.904000] usb 4-2: device not accepting address 10, error -110
[17619971.016000] usb 4-2: new full speed USB device using uhci_hcd and address 11
[17619981.424000] usb 4-2: device not accepting address 11, error -110
[17621009.180000] usb 4-2: new full speed USB device using uhci_hcd and address 12
[17621012.292000] usb 4-2: device descriptor read/64, error -110
[17621018.756000] usb 4-2: new full speed USB device using uhci_hcd and address 13
[17621021.276000] usb 4-2: new full speed USB device using uhci_hcd and address 14
[17621141.480000] usb 4-2: new full speed USB device using uhci_hcd and address 15
[17621141.624000] scsi6 : SCSI emulation for USB Mass Storage devices
[17621141.624000] usb-storage: device found at 15
[17621141.624000] usb-storage: waiting for device to settle before scanning
[17621142.500000] usb 4-2: USB disconnect, address 15
[17621178.524000] usb 4-2: new full speed USB device using uhci_hcd and address 16
[17621178.668000] scsi7 : SCSI emulation for USB Mass Storage devices
[17621178.668000] usb-storage: device found at 16
[17621178.668000] usb-storage: waiting for device to settle before scanning
[17621183.672000]   Vendor: FUJIFILM  Model: USB-DRIVEUNIT     Rev: 1.00
[17621183.672000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17621183.680000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[17621183.688000] sdb: Write Protect is off
[17621183.688000] sdb: Mode Sense: 0b 00 00 08
[17621183.688000] sdb: assuming drive cache: write through
[17621183.708000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[17621183.712000] sdb: Write Protect is off
[17621183.712000] sdb: Mode Sense: 0b 00 00 08
[17621183.712000] sdb: assuming drive cache: write through
[17621183.712000]  sdb: sdb1
[17621183.736000] sd 7:0:0:0: Attached scsi removable disk sdb
[17621183.736000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[17621183.736000] usb-storage: device scan complete
[17621185.160000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17621446.664000] usb 4-2: USB disconnect, address 16
[17621446.764000]  7:0:0:0: rejecting I/O to dead device

---

### Post by Geryon on 2006-08-08
Wow, that is the EXACT problem I am having.  Whenever I use a USB mass storage device, be it an external hard drive or memory stick and I start to copy on or off large amounts of data the device "dissapears".  

I see similiar errors as well:

```

[17179694.744000] usb 1-2: new high speed USB device using ehci_hcd and address 3
[17179706.288000] usb 1-2: device not accepting address 3, error -110
[17179706.588000] usb 1-2: new high speed USB device using ehci_hcd and address 5
[17179718.132000] usb 1-2: device not accepting address 5, error -110
[17179718.432000] usb 1-2: new high speed USB device using ehci_hcd and address 7
[17179729.976000] usb 1-2: device not accepting address 7, error -110
[17179730.276000] usb 1-2: new high speed USB device using ehci_hcd and address 9
[17179741.820000] usb 1-2: device not accepting address 9, error -110
[17179742.120000] usb 1-2: new high speed USB device using ehci_hcd and address 11
[17179753.664000] usb 1-2: device not accepting address 11, error -110

```

I am running Dapper and did _NOT_ have this problem with the exact same hardware under Breezy Badger.  

I am running this on an Averatec 3200 system.

```

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

```

And I noticed that both the 'uhci_hcd' and 'ehci_hcd' modules are loaded.    Is it okay to have both the universal and enhanced USB host modules loaded together???

Jeeze, I am troubleshooting as I write this...

THat was it.  I 'rmmod ehci_hcd' and voila, the USB is working like a champ!  So that's the solution :)  
[B][SIZE="4"]
Remove the 'ehci_hcd' module.[/SIZE][/B]

---

### Post by Geryon on 2006-08-08
Okay, so I am replying to myself here.

I didn't realize that 'ehci-hcd' is the USB 2.0 support.  While the device works flawlessly wihtout ehci-hcd the speed is USB 1.1 speeds...  Intolerable for working with a USB hard drive.  

So the "solution" I posted earlier is only a temporary work-around.

---

### Post by skorange on 2006-08-17
I'm having the same issue with the same results as above.

How does "rmmod" work?  What are these "mods" anyway? Would it be possible to disable a usb 1 mod instead of the ehci usb 2.0 one?

---

### Post by donatell0 on 2007-03-10
That was necessary for me to get my canon sd600 camera to work as well. Please post if there is any way to get it to work in USB 2.0 mode.

---

### Post by louisgag on 2007-04-09
I have a very similar problem in Ubuntu 6.10 when I plugged either my 2gb or 40gb usb-powered usb2.0 drives. My 256mb drive gets detected without any problem. My 2 & 40gb drives don't get detected and aren't listed in /dev. Also, _modprobe -r ehci_hcd_ won't help at all.

_My demesg_
```

 778.757567] usb 2-1.1: new full speed USB device using ohci_hcd and address 8
[  778.865524] usb 2-1.1: configuration #1 chosen from 1 choice
[  779.087411] usbcore: registered new driver libusual
[  779.244327] SCSI subsystem initialized
[  779.290184] Initializing USB Mass Storage driver...
[  779.291284] scsi0 : SCSI emulation for USB Mass Storage devices
[  779.292314] usb-storage: device found at 8
[  779.292323] usb-storage: waiting for device to settle before scanning
[  779.292351] usbcore: registered new driver usb-storage
[  779.292361] USB Mass Storage support registered.
[  784.286378] usb-storage: device scan complete
[  789.851058] usb 2-1.1: reset full speed USB device using ohci_hcd and address 8
[  792.919493] usb 2-1.1: device descriptor read/64, error -110
[  808.075944] usb 2-1.1: device descriptor read/64, error -110
[  808.256682] usb 2-1.1: reset full speed USB device using ohci_hcd and address 8
[  811.324133] usb 2-1.1: device descriptor read/64, error -110
[  826.481575] usb 2-1.1: device descriptor read/64, error -110
[  826.661308] usb 2-1.1: reset full speed USB device using ohci_hcd and address 8

```

---

### Post by louisgag on 2007-04-09
Ok I just solved my problem!!!

I was plugging the drive into my usb hub, and it was apparently not providing enough power to the drive. Now that I plug my drive directly into the computer, it works!!!

_My new dmesg_

```


  748.817861] ohci_hcd 0000:00:02.3: wakeup
[  749.198674] usb 2-1: new full speed USB device using ohci_hcd and address 4
[  749.408367] usb 2-1: configuration #1 chosen from 1 choice
[  749.614863] usbcore: registered new driver libusual
[  749.737386] SCSI subsystem initialized
[  749.744785] Initializing USB Mass Storage driver...
[  749.744989] scsi0 : SCSI emulation for USB Mass Storage devices
[  749.745086] usb-storage: device found at 4
[  749.745090] usb-storage: waiting for device to settle before scanning
[  749.745110] usbcore: registered new driver usb-storage
[  749.745115] USB Mass Storage support registered.
[  754.737387] usb-storage: device scan complete
[  754.766345]   Vendor: FUJITSU   Model: MHV2040AH         Rev: 0811
[  754.766364]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  754.861208] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[  754.878140] sda: test WP failed, assume Write Enabled
[  754.878152] sda: assuming drive cache: write through
[  754.889118] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[  754.906094] sda: test WP failed, assume Write Enabled
[  754.906106] sda: assuming drive cache: write through
[  754.906275]  sda: sda1
[  754.935747] sd 0:0:0:0: Attached scsi disk sda
[  754.971698] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  756.131664] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


```

---

### Post by ras on 2008-01-01
> **Geryon said:**
> 

Jeeze, I am troubleshooting as I write this...

THat was it.  I 'rmmod ehci_hcd' and voila, the USB is working like a champ!  So that's the solution :)  
[B][SIZE="4"]
Remove the 'ehci_hcd' module.[/SIZE][/B]

I can confirm that this solution worked in my situation. Toshiba Satellite with Ubuntu 7.10 (Gutsy) and Sony Handycam HDD DCR-SR82.

---

### Post by Daelyn on 2008-01-01
> **ras said:**
> I can confirm that this solution worked in my situation. Toshiba Satellite with Ubuntu 7.10 (Gutsy) and Sony Handycam HDD DCR-SR82.

But, by doing this you will get "intolerable" speeds from your USB devices because they will revert to USB v 1.1 which is way slower.

Are you using a USB hub? If so, what happens if you plug in your handycam directly to the computer instead?

---

### Post by donatell0 on 2008-01-01
Yes, this is a problem. The USB works at sad speeds. I would like to know there is a solution for this. I am not using a hub but I hope that my cabinet does not implement a hub internally!

---

