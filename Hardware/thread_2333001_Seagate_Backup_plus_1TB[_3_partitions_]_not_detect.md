---
title: "Seagate Backup plus 1TB[ 3 partitions ] not detected"
date: 2016-08-06
forum: Hardware
---

### Post by the-sumit67 on 2016-08-06
I am using Ubuntu 14.04

I have same problem as mentioned here [http://askubuntu.com/questions/396196/backup-drive-issue-seagate-backup-plus-1tb-in-not-getting-detected](http://askubuntu.com/questions/396196/backup-drive-issue-seagate-backup-plus-1tb-in-not-getting-detected)

lsusb can show it, but after trying so many times, i am unable to get it working.

$ lsusb
Bus 002 Device 003: ID 04f2:b2e2 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 025: ID 0bc2:a003 Seagate RSS LLC Backup Plus
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If this hard drive is incompatible with Ubuntu, then please tell me which hard drive(brand/model) should i buy, and which external hard drives you guys are using on ubuntu.

---

### Post by weatherman2 on 2016-08-06
Is your Seagate using encryption?  (Seagate security software of some sort?)  If so, it almost certainly won't work in Linux unless you re-format the drive and use partitions that aren't encrypted.

I've used many portable/external USB drives in Linux over the years, and I've never found one that was not compatible automatically.  But none of these drives used encryption.

---

### Post by the-sumit67 on 2016-08-06
Thank you for replying...

1 out of 3 partition is encrypted via truerypt. Is this the reason of my problem ?

I am not using any kind of seagate backup or encryption software. Other two partitions are NTFS, so i guess at least these two partition should show up, but nothing happens.

---

### Post by weatherman2 on 2016-08-06
No, a Truecrypt partition should not cause any issues.  I use Truecrypt in Ubuntu routinely.

Open a terminal (Ctrl Alt t) and type this command, then please give the output here:

```

sudo parted -l

```

---

### Post by the-sumit67 on 2016-08-06
```

asx@ExMac:~$ sudo lsusb
[sudo] password for asx: 
Bus 002 Device 003: ID 04f2:b2e2 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 0bc2:a003 Seagate RSS LLC Backup Plus
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
asx@ExMac:~$ sudo parted -l
Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  525MB   524MB   primary   ntfs            boot
 2      525MB   64.0GB  63.4GB  primary   ntfs
 3      64.0GB  169GB   105GB   primary   ntfs
 4      169GB   500GB   331GB   extended                  lba
 5      169GB   232GB   62.9GB  logical   ntfs
 6      232GB   238GB   6499MB  logical   linux-swap(v1)
 7      238GB   284GB   45.9GB  logical   ext4
 8      284GB   500GB   216GB   logical




asx@ExMac:~$ 



```

---

### Post by weatherman2 on 2016-08-06
OK, clearly the drive isn't showing up at a hard drive at all.  Try looking at the output of the "dmesg" command.  You could try filtering for "usb" or other keywords, like this:

```

dmesg | grep usb

```

And just parsing manually through the output of "dmesg" to look for error messages and clues.

What kind of computer are you plugging the drive into?  Are all of the USB ports USB 3.0 or 2.0?  Try different ports.

You might also boot Ubuntu 16.04 from live USB and then see if the drive is detected with that.  If so, maybe you can update the kernel in 14.04 or something or just update to 16.04.

---

### Post by the-sumit67 on 2016-08-06
```

[    0.337816] usbcore: registered new interface driver usbfs
[    0.337825] usbcore: registered new interface driver hub
[    0.337848] usbcore: registered new device driver usb
[    4.020113] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.020115] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.020117] usb usb1: Product: EHCI Host Controller
[    4.020119] usb usb1: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    4.020120] usb usb1: SerialNumber: 0000:00:1a.0
[    4.036203] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.036205] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.036207] usb usb2: Product: EHCI Host Controller
[    4.036209] usb usb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    4.036210] usb usb2: SerialNumber: 0000:00:1d.0
[    4.036775] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    4.036777] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.036779] usb usb3: Product: xHCI Host Controller
[    4.036781] usb usb3: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    4.036782] usb usb3: SerialNumber: 0000:00:14.0
[    4.037399] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    4.037401] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.037403] usb usb4: Product: xHCI Host Controller
[    4.037404] usb usb4: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    4.037406] usb usb4: SerialNumber: 0000:00:14.0
[    4.332115] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    4.464269] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    4.464273] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.575957] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    4.708144] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    4.708148] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.779896] usb 1-1.3: new full-speed USB device number 3 using ehci-pci
[    4.875785] usb 1-1.3: New USB device found, idVendor=0489, idProduct=e032
[    4.875795] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.875801] usb 1-1.3: Product: BCM20702A0
[    4.875806] usb 1-1.3: Manufacturer: Broadcom Corp
[    4.875810] usb 1-1.3: SerialNumber: 083E8EADFD56
[    4.947752] usb 1-1.4: new high-speed USB device number 4 using ehci-pci
[    5.040444] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=0129
[    5.040448] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.040450] usb 1-1.4: Product: USB2.0-CRW
[    5.040451] usb 1-1.4: Manufacturer: Generic
[    5.040453] usb 1-1.4: SerialNumber: 20100201396000000
[    5.045013] usbcore: registered new interface driver rtsx_usb
[    5.111758] usb 2-1.6: new high-speed USB device number 3 using ehci-pci
[    5.219345] usb 2-1.6: New USB device found, idVendor=04f2, idProduct=b2e2
[    5.219350] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.219353] usb 2-1.6: Product: Lenovo EasyCamera
[    5.219356] usb 2-1.6: Manufacturer: Chicony Corp.
[   16.096390] usbcore: registered new interface driver btusb
[   16.100666] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input12
[   16.100740] usbcore: registered new interface driver uvcvideo
[  142.053725] usb 4-3: new SuperSpeed USB device number 3 using xhci_hcd
[  142.072885] usb 4-3: New USB device found, idVendor=0bc2, idProduct=a003
[  142.072896] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  142.072903] usb 4-3: Product: Backup+ BK
[  142.072908] usb 4-3: Manufacturer: Seagate 
[  142.072912] usb 4-3: SerialNumber: NA53S4R1
[  142.155279] usbcore: registered new interface driver usb-storage
[  142.733405] usb 4-3: USB disconnect, device number 3
[  148.750000] usb 4-3: new SuperSpeed USB device number 4 using xhci_hcd
[  148.769501] usb 4-3: New USB device found, idVendor=0bc2, idProduct=a003
[  148.769512] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  148.769517] usb 4-3: Product: Backup+ BK
[  148.769522] usb 4-3: Manufacturer: Seagate 
[  148.769527] usb 4-3: SerialNumber: NA53S4R1
[  149.129886] usb 4-3: USB disconnect, device number 4
[  149.369976] usb 4-3: new SuperSpeed USB device number 5 using xhci_hcd
[  149.387125] usb 4-3: New USB device found, idVendor=0bc2, idProduct=a003
[  149.387136] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  149.387141] usb 4-3: Product: Backup+ BK
[  149.387146] usb 4-3: Manufacturer: Seagate 
[  149.387151] usb 4-3: SerialNumber: NA53S4R1
[ 2533.491811] usb 4-3: USB disconnect, device number 5
[ 6083.196641] usb 3-3: new high-speed USB device number 4 using xhci_hcd
[ 6107.764046] usb 3-3: new high-speed USB device number 8 using xhci_hcd
[ 6107.894982] usb 3-3: New USB device found, idVendor=0bc2, idProduct=a003
[ 6107.894993] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6107.894999] usb 3-3: Product: Backup+ BK
[ 6107.895004] usb 3-3: Manufacturer: Seagate 
[ 6107.895008] usb 3-3: SerialNumber: NA53S4R1



```

It looks like usb drive gets automatically disconneted.. I have PMed you a link of complete output of "dmesg".

I am on Lenovo G580 laptop. 2 ports USB3, and 1 USB2. I have already tried all the ports.

Now i am going to update kernel, and check with 16.04.

---

### Post by weatherman2 on 2016-08-07
I think you're right - the drive is disconnecting automatically after a few attempts.  Not sure why.

I would boot the live USB of 16.04 first before going through all the trouble of updating to 16.04, because if the problem isn't fixed there, you may have done it for nothing.

---

### Post by the-sumit67 on 2016-08-07
HDD was working fine with 16.04 live usb, so I performed a clean install it and now everything is fine...

Thanks a lot...

---

