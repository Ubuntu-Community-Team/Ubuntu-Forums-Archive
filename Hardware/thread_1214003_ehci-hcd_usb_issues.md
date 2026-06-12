---
title: "ehci-hcd usb issues"
date: 2009-07-15
forum: Hardware
---

### Post by poboy975 on 2009-07-15
hi I've been going through posts here and so far have not been able to find any answers. I have a usb flash drive that works fine. I lplugged in a 250gig monsoon 7200rpm external drive, and nothing happens. dmesg gives me this

[   29.128543] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1182.823419] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1193.712226] wlan1: no IPv6 routers present
[ 2588.912107] udev: starting version 141
[ 3095.384246] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 3095.594073] usb 1-3: configuration #1 chosen from 1 choice
[ 3179.576295] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 3179.762088] usb 1-1: configuration #1 chosen from 1 choice
[ 3179.829008] Initializing USB Mass Storage driver...
[ 3179.831665] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3179.833024] usbcore: registered new interface driver usb-storage
[ 3179.833035] USB Mass Storage support registered.
[ 3179.881767] usb-storage: device found at 3
[ 3179.881776] usb-storage: waiting for device to settle before scanning
[ 3184.880474] usb-storage: device scan complete
[ 3191.120183] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3201.364268] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3217.612065] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3217.860046] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3228.104204] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3228.237084] scsi 2:0:0:0: Device offlined - not ready after error recovery
[ 3233.451975] usb 1-3: USB disconnect, address 2
[ 3237.421225] usb 1-1: USB disconnect, address 3
[ 3242.560265] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 3242.764901] usb 1-1: configuration #1 chosen from 1 choice
[ 3242.816161] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3242.823184] usb-storage: device found at 4
[ 3242.823188] usb-storage: waiting for device to settle before scanning
[ 3247.820409] usb-storage: device scan complete
[ 3254.115079] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[ 3264.356080] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[ 3280.612075] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[ 3280.860042] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[ 3291.104257] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[ 3291.237136] scsi 3:0:0:0: Device offlined - not ready after error recovery
[ 3295.111148] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 3352.753624] usb 1-1: USB disconnect, address 4
[ 3358.988244] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 3359.181583] usb 1-3: configuration #1 chosen from 1 choice
[ 3359.220340] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3359.231683] usb-storage: device found at 5
[ 3359.231687] usb-storage: waiting for device to settle before scanning
[ 3364.228296] usb-storage: device scan complete
[ 3370.112248] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 3380.356272] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 3386.389950] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3396.600148] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 3396.848082] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 3407.092244] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 3407.225007] scsi 4:0:0:0: Device offlined - not ready after error recovery
[ 3422.148801] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3432.412133] wlan1: no IPv6 routers present
[ 4287.736251] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 4287.921230] usb 1-1: configuration #1 chosen from 1 choice
[ 4287.982473] scsi5 : SCSI emulation for USB Mass Storage devices
[ 4287.994584] usb-storage: device found at 6
[ 4287.994592] usb-storage: waiting for device to settle before scanning
[ 4292.992379] usb-storage: device scan complete
[ 4292.992994] scsi 5:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[ 4293.045490] sd 5:0:0:0: [sdb] 15646656 512-byte hardware sectors: (8.01 GB/7.45 GiB)
[ 4293.051595] sd 5:0:0:0: [sdb] Write Protect is off
[ 4293.051606] sd 5:0:0:0: [sdb] Mode Sense: 65 44 09 30
[ 4293.051613] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4293.063451] sd 5:0:0:0: [sdb] 15646656 512-byte hardware sectors: (8.01 GB/7.45 GiB)
[ 4293.068926] sd 5:0:0:0: [sdb] Write Protect is off
[ 4293.068936] sd 5:0:0:0: [sdb] Mode Sense: 65 44 09 30
[ 4293.068943] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4293.068957]  sdb: sdb1
[ 4293.071029] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 4293.071207] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4318.964389] usb 1-1: USB disconnect, address 6
[ 4318.967186] Buffer I/O error on device sdb1, logical block 1
[ 4318.967196] lost page write due to I/O error on sdb1
[ 4318.967220] Buffer I/O error on device sdb1, logical block 30563
[ 4318.967227] lost page write due to I/O error on sdb1
[ 4318.967238] Buffer I/O error on device sdb1, logical block 30565
[ 4318.967245] lost page write due to I/O error on sdb1
[ 4628.005292] usb 1-3: USB disconnect, address 5
[ 4635.312084] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 4635.508800] usb 1-3: configuration #1 chosen from 1 choice
[ 4635.548567] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4635.559051] usb-storage: device found at 7
[ 4635.559055] usb-storage: waiting for device to settle before scanning
[ 4640.557180] usb-storage: device scan complete
[ 4647.116813] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 4657.400235] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 4673.644095] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 4673.892337] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 4684.136240] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 4684.269062] scsi 6:0:0:0: Device offlined - not ready after error recovery

when I try modprobe ehci_hcd it say not found. I've seen others with this issue, have there been any answers? I have a dell Inspiron 8600 with ubuntu jaunty 9.04 installed and latest updates applied. I would appreciate a solution to this problem. thanks

lsusb lists this:
Bus 001 Device 007: ID 13fd:0540 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by rygle on 2009-09-17
There have been multiple bugs logged in Launchpad about this and very similar ehci-hcd/ohci-hcd/uhci-hcd problems that cause the USB subsystem to be reset repeatedly under moderate load. This has been going on since at least 2007, and nobody seems to want to fix it. Still happening in 9.04.

This bug doesn't seem unique to Ubuntu, but it crops up in other distro's too, which suggests strongly that it may be kernel related. Some suggest that it is happening due to compiz or some other compiz like software, but several of the bug reporters clearly state they are not using compiz or similar. It also seems to affect at least Ubuntu and Xubuntu - not sure about Kubuntu.

Sometimes it makes the keys repeat randomly. Sometimes it interferes with the basic responsiveness of the mouse or keyboard. Sometimes it causes USB mass storage devices to be unmounted during a read or write, in some cases causing data corruption.

It seems that, given the prevalence of USB, this is one of the most pressing bugs in Linux. Yet nobody seems to care. Doesn't seem to say much for Linux when one of the most depended on system buses is completely unreliable.

---

### Post by ajm8127 on 2009-10-17
I'm noticing the same behavior with my new LG env touch. This is the firmest lead yet as to what is going wrong. Is there any software work around, or should I just use a card reader?

---

### Post by giannakp on 2009-10-17
Same here :
```
Oct 17 14:49:18 spartakos kernel: [58267.392024] usb 1-7: new high speed USB device using ehci_hcd and address 11
Oct 17 14:49:18 spartakos kernel: [58267.526818] usb 1-7: configuration #1 chosen from 1 choice
Oct 17 14:49:18 spartakos kernel: [58267.527536] scsi8 : SCSI emulation for USB Mass Storage devices
Oct 17 14:49:18 spartakos kernel: [58267.527621] usb-storage: device found at 11
Oct 17 14:49:18 spartakos kernel: [58267.527622] usb-storage: waiting for device to settle before scanning
Oct 17 14:49:23 spartakos kernel: [58272.524236] usb-storage: device scan complete
Oct 17 14:49:23 spartakos kernel: [58272.526162] scsi 8:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Oct 17 14:49:23 spartakos kernel: [58272.529823] sd 8:0:0:0: [sdd] Attached SCSI disk
Oct 17 14:49:23 spartakos kernel: [58272.529920] sd 8:0:0:0: Attached scsi generic sg4 type 0
Oct 17 14:49:36 spartakos kernel: [58284.949185] usb 1-7: USB disconnect, address 11
Oct 17 14:49:48 spartakos kernel: [58296.884043] usb 1-7: new high speed USB device using ehci_hcd and address 12
Oct 17 14:49:48 spartakos kernel: [58297.018261] usb 1-7: configuration #1 chosen from 1 choice
Oct 17 14:49:48 spartakos kernel: [58297.021310] scsi9 : SCSI emulation for USB Mass Storage devices
Oct 17 14:49:48 spartakos kernel: [58297.022532] usb-storage: device found at 12
Oct 17 14:49:48 spartakos kernel: [58297.022535] usb-storage: waiting for device to settle before scanning
Oct 17 14:49:53 spartakos kernel: [58302.020316] usb-storage: device scan complete
Oct 17 14:49:53 spartakos kernel: [58302.022399] scsi 9:0:0:0: Direct-Access     WDC WD25 00KS-00MJB0      1C03 PQ: 0 ANSI: 2 CCS
Oct 17 14:49:53 spartakos kernel: [58302.023886] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Oct 17 14:49:53 spartakos kernel: [58302.029175] sd 9:0:0:0: [sdd] Write Protect is off
Oct 17 14:49:53 spartakos kernel: [58302.029180] sd 9:0:0:0: [sdd] Mode Sense: 00 38 00 00
Oct 17 14:49:53 spartakos kernel: [58302.029182] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Oct 17 14:49:53 spartakos kernel: [58302.037054] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Oct 17 14:49:53 spartakos kernel: [58302.038243] sd 9:0:0:0: [sdd] Write Protect is off
Oct 17 14:49:53 spartakos kernel: [58302.038245] sd 9:0:0:0: [sdd] Mode Sense: 00 38 00 00
Oct 17 14:49:53 spartakos kernel: [58302.038247] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Oct 17 14:49:53 spartakos kernel: [58302.038254]  sdd: sdd1
Oct 17 14:49:53 spartakos kernel: [58302.042391] sd 9:0:0:0: [sdd] Attached SCSI disk
Oct 17 14:49:53 spartakos kernel: [58302.042452] sd 9:0:0:0: Attached scsi generic sg4 type 0
Oct 17 14:50:25 spartakos kernel: [58333.916039] usb 1-7: reset high speed USB device using ehci_hcd and address 12
Oct 17 14:50:25 spartakos kernel: [58334.120038] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:25 spartakos kernel: [58334.436033] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:25 spartakos kernel: [58334.648043] usb 1-7: reset high speed USB device using ehci_hcd and address 12
Oct 17 14:50:26 spartakos kernel: [58334.854224] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:26 spartakos kernel: [58335.160033] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:26 spartakos kernel: [58335.377022] usb 1-7: reset high speed USB device using ehci_hcd and address 12
Oct 17 14:50:27 spartakos kernel: [58335.844026] usb 1-7: device not accepting address 12, error -71
Oct 17 14:50:27 spartakos kernel: [58335.956027] usb 1-7: reset high speed USB device using ehci_hcd and address 12
Oct 17 14:50:27 spartakos kernel: [58336.420029] usb 1-7: device not accepting address 12, error -71
Oct 17 14:50:27 spartakos kernel: [58336.420067] sd 9:0:0:0: Device offlined - not ready after error recovery
Oct 17 14:50:27 spartakos kernel: [58336.420076] sd 9:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 17 14:50:27 spartakos kernel: [58336.420079] end_request: I/O error, dev sdd, sector 413663535
Oct 17 14:50:27 spartakos kernel: [58336.420083] Buffer I/O error on device sdd1, logical block 51707934
Oct 17 14:50:27 spartakos kernel: [58336.420085] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420092] Buffer I/O error on device sdd1, logical block 51707935
Oct 17 14:50:27 spartakos kernel: [58336.420093] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420096] Buffer I/O error on device sdd1, logical block 51707936
Oct 17 14:50:27 spartakos kernel: [58336.420097] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420100] Buffer I/O error on device sdd1, logical block 51707937
Oct 17 14:50:27 spartakos kernel: [58336.420101] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420104] Buffer I/O error on device sdd1, logical block 51707938
Oct 17 14:50:27 spartakos kernel: [58336.420105] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420108] Buffer I/O error on device sdd1, logical block 51707939
Oct 17 14:50:27 spartakos kernel: [58336.420109] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420112] Buffer I/O error on device sdd1, logical block 51707940
Oct 17 14:50:27 spartakos kernel: [58336.420113] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420116] Buffer I/O error on device sdd1, logical block 51707941
Oct 17 14:50:27 spartakos kernel: [58336.420118] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420120] Buffer I/O error on device sdd1, logical block 51707942
Oct 17 14:50:27 spartakos kernel: [58336.420121] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420124] Buffer I/O error on device sdd1, logical block 51707943
Oct 17 14:50:27 spartakos kernel: [58336.420125] lost page write due to I/O error on sdd1
Oct 17 14:50:27 spartakos kernel: [58336.420154] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420158] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420200] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420227] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420232] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420236] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420239] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420243] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420247] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420251] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420261] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420265] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420269] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420273] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420276] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420280] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420284] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420287] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420291] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420294] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420298] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420302] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420306] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420309] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420313] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420317] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420327] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420333] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420337] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420341] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420345] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420349] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420353] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420360] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420364] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420368] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420375] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420379] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420383] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420388] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420394] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420398] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420407] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420411] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420414] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420458] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420499] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420540] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420582] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420622] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420638] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420642] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420647] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420651] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420655] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420658] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420661] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420665] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420674] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420677] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420681] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420685] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420688] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420692] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420696] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420700] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420703] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420707] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420711] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420715] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420719] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420723] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420726] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420730] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420738] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420742] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420745] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420749] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420774] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420778] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420816] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420855] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420892] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420928] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420967] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420970] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420974] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420978] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420981] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420985] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.420994] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421031] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421068] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421105] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421140] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421177] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421214] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421252] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421290] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421313] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421350] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421388] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421426] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421467] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421494] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421498] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421507] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421511] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421514] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421518] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421522] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421525] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421529] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421533] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421537] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421541] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421545] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421585] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421589] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421632] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421655] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421661] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421670] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421674] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421682] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421692] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421698] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421701] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421707] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421712] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421717] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421721] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421725] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421730] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421735] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421738] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421743] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421746] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421755] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421758] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421762] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421766] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421771] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421774] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421778] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421781] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421787] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421791] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421794] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421798] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421801] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421809] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421813] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.421848] sd 9:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 17 14:50:27 spartakos kernel: [58336.421851] end_request: I/O error, dev sdd, sector 413663775
Oct 17 14:50:27 spartakos kernel: [58336.424066] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424084] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424087] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424092] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424135] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424141] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424154] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424158] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424173] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424177] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424181] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424185] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424206] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424211] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424214] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424218] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424251] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424258] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424266] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424270] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424292] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424296] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424301] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424306] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424340] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424343] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424347] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424359] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424379] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424384] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424388] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424392] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424409] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424413] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424417] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424421] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424451] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424458] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424464] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424468] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424486] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424490] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424494] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424499] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424522] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424527] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424531] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424536] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424583] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424589] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424595] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424608] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424792] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424819] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424848] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.424877] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425066] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425095] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425124] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425154] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425192] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425203] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425207] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425212] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425238] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425245] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425249] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425253] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425415] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425444] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425460] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425491] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425658] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425688] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425716] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425740] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425764] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425769] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425772] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425776] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425791] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425794] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425798] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425802] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425817] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425821] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425824] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425828] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425853] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425857] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425860] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425864] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425882] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425887] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425891] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425895] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425910] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425914] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425917] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425921] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425947] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425951] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425955] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425959] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425974] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425978] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425982] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.425986] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426000] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426004] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426008] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426012] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426026] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426030] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426034] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426038] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426058] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426062] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426065] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426069] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426084] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426089] sd 9:0:0:0: rejecting I/O to offline device
Oct 17 14:50:27 spartakos kernel: [58336.426108] JBD: recovery failed
Oct 17 14:50:27 spartakos kernel: [58336.426111] EXT3-fs: error loading journal.
Oct 17 14:50:27 spartakos kernel: [58336.440883] usb 1-7: USB disconnect, address 12
Oct 17 14:50:27 spartakos kernel: [58336.556033] usb 1-7: new high speed USB device using ehci_hcd and address 13
Oct 17 14:50:28 spartakos kernel: [58336.761038] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:28 spartakos kernel: [58337.068034] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:28 spartakos kernel: [58337.284030] usb 1-7: new high speed USB device using ehci_hcd and address 14
Oct 17 14:50:28 spartakos kernel: [58337.489042] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:29 spartakos kernel: [58337.797045] usb 1-7: device descriptor read/64, error -71
Oct 17 14:50:29 spartakos kernel: [58338.012044] usb 1-7: new high speed USB device using ehci_hcd and address 15
Oct 17 14:50:29 spartakos kernel: [58338.484357] usb 1-7: device not accepting address 15, error -71
Oct 17 14:50:29 spartakos kernel: [58338.593053] usb 1-7: new high speed USB device using ehci_hcd and address 16
Oct 17 14:50:30 spartakos kernel: [58339.060028] usb 1-7: device not accepting address 16, error -71
Oct 17 14:50:30 spartakos kernel: [58339.060047] hub 1-0:1.0: unable to enumerate USB device on port 7
Oct 17 14:50:30 spartakos kernel: [58339.524033] usb 2-7: new full speed USB device using ohci_hcd and address 10
Oct 17 14:50:30 spartakos kernel: [58339.704025] usb 2-7: device descriptor read/64, error -62
Oct 17 14:50:31 spartakos kernel: [58339.988022] usb 2-7: device descriptor read/64, error -62
Oct 17 14:50:31 spartakos kernel: [58340.268047] usb 2-7: new full speed USB device using ohci_hcd and address 11
Oct 17 14:50:31 spartakos kernel: [58340.448022] usb 2-7: device descriptor read/64, error -62
Oct 17 14:50:31 spartakos kernel: [58340.732021] usb 2-7: device descriptor read/64, error -62
Oct 17 14:50:32 spartakos kernel: [58341.012018] usb 2-7: new full speed USB device using ohci_hcd and address 12
Oct 17 14:50:32 spartakos kernel: [58341.420021] usb 2-7: device not accepting address 12, error -62
Oct 17 14:50:32 spartakos kernel: [58341.596027] usb 2-7: new full speed USB device using ohci_hcd and address 13
Oct 17 14:50:33 spartakos kernel: [58342.004026] usb 2-7: device not accepting address 13, error -62
Oct 17 14:50:33 spartakos kernel: [58342.004042] hub 2-0:1.0: unable to enumerate USB device on port 7
```

Some people suggest as solution "sudo modprobe -r ehci_hcd" but in my system this module is not loaded.

Kernel : 2.6.28-15-generic
Ubuntu : 9.04 jaunty amd64

Any solution?

---

### Post by ajm8127 on 2009-10-17
So I primarily bought the phone for the MP3 player, so it gives me a kind of determination to make this work. 

I checked for module echi_hcd and it is not running. 

```
omniscient@GoSteelers:~$ sudo modprobe -l | grep ehci
omniscient@GoSteelers:~$ sudo modprobe -l | grep hci
kernel/drivers/ieee1394/ohci1394.ko
kernel/drivers/usb/host/whci/whci-hcd.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/mmc/host/sdhci.ko
kernel/drivers/mmc/host/sdhci-pci.ko
kernel/drivers/firewire/firewire-ohci.ko
kernel/drivers/uwb/whci.ko
omniscient@GoSteelers:~$ 

```

I see whci, which is for wireless devices, right?  I also see ohci1394, for firewire I would think. So what controls the host interface for usb?

I am familiar with c, and would like to work towards finding a solution for this problem.

---

### Post by giannakp on 2009-10-17
> **ajm8127 said:**
> 
I see whci, which is for wireless devices, right?  I also see ohci1394, for firewire I would think. So what controls the host interface for usb?

I am familiar with c, and would like to work towards finding a solution for this problem.

This module it existed until kernel of Ubuntu 8.10. After Ubuntu 9.04 it changed the relative sub system of the kernel.

---

### Post by ajm8127 on 2009-10-17
I see. I happen to have 8.10 on my system still. I booted into it and here is the relevent output:

```
[  126.568013] usb 3-4: new high speed USB device using ehci_hcd and address 4
[  126.624022] hub 3-0:1.0: unable to enumerate USB device on port 4
[  126.940010] usb 3-4: new high speed USB device using ehci_hcd and address 5
[  127.097026] usb 3-4: configuration #1 chosen from 1 choice
[  127.203299] usbcore: registered new interface driver libusual
[  127.222776] Initializing USB Mass Storage driver...
[  127.227358] scsi4 : SCSI emulation for USB Mass Storage devices
[  127.228642] usbcore: registered new interface driver usb-storage
[  127.228872] USB Mass Storage support registered.
[  127.229156] usb-storage: device found at 5
[  127.229160] usb-storage: waiting for device to settle before scanning
[  133.228075] usb-storage: device scan complete
[  138.840016] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  139.096014] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  144.348018] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  144.604026] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  144.743544] scsi 4:0:0:0: Device offlined - not ready after error recovery
omniscient@silverback:~$ modprobe -l | grep ehci
/lib/modules/2.6.27-11-generic/kernel/drivers/usb/host/ehci-hcd.ko
omniscient@silverback:~$ 


```

So what you are saying is that the usb host interface has now been incorporated into the kernel, correct?

---

### Post by giannakp on 2009-10-18
> **ajm8127 said:**
> So what you are saying is that the usb host interface has now been incorporated into the kernel, correct?

I have 9.04 jaunty x86_64 and kernel 2.6.28-15-generic.

Typing : "modprobe -l | grep ehci" the result is nothing.
Since 9.04 the USB 2.0 sub system has been incorporated into the kernel.

In your system the command: "sudo modprobe -r ehci_hcd", i think  that will solve your problem but then you will have USB 1.0 speed.

---

### Post by ajm8127 on 2009-10-18
> **giannakp said:**
> I have 9.04 jaunty x86_64 and kernel 2.6.28-15-generic.

Typing : "modprobe -l | grep ehci" the result is nothing.
Since 9.04 the USB 2.0 sub system has been incorporated into the kernel.

In your system the command: "sudo modprobe -r ehci_hcd", i think  that will solve your problem but then you will have USB 1.0 speed.

I think my last post was kind of confusing. I have both 9.04 and 8.10 on my system. In 9.04 

```
modprobe -l | grep ehci
```

results in nothing because the module ehci_hcd hs been incorporated into the kernel as we have learned. So in 9.04 

```
modprobe -r ehci_hcd
```

would do no good because ehci_hcd is not running as a module in the first place. 

I only posted that output from 8.10 to show that the ehci_hcd module is independent there, and in 9.04 it is part of the kernel. 

The bottom line seems to come from rygle:
> There have been multiple bugs logged in Launchpad about this and very similar ehci-hcd/ohci-hcd/uhci-hcd problems that cause the USB subsystem to be reset repeatedly under moderate load. This has been going on since at least 2007, and nobody seems to want to fix it. Still happening in 9.04.

I am going to fool around a bit with my older installation and see what happens.

---

### Post by bsmith1051 on 2009-10-18
> **rygle said:**
> It seems that, given the prevalence of USB, this is one of the most pressing bugs in Linux. Yet nobody seems to care. Doesn't seem to say much for Linux when one of the most depended on system buses is completely unreliable.
This post of yours was outstanding.  I wish I could 'mod' you up, or give you a gold star like in the old forums!

---

### Post by rygle on 2009-10-29
> **bsmith1051 said:**
> This post of yours was outstanding.  I wish I could 'mod' you up, or give you a gold star like in the old forums!

I'd be happy just to have a usable Ubuntu O/S. Sadly at present I've reverted to Windows. Even though pretty much all my software needs were being met by Ubuntu, the USB/EHCI related 5-times-a-day system crashes were driving me completely nuts. I'm keeping dual boot working and watching for improvements, but even today I got a kernel panic (flashing caps lock light) when typing into a dialogue in Firefox - typing about this very issue.

---

### Post by rygle on 2009-10-29
Here's an interesting link;
[http://manpages.ubuntu.com/manpages/hardy/man4/ehci.4.html]("http://manpages.ubuntu.com/manpages/hardy/man4/ehci.4.html")

The most notable thing is this;
> The driver is not finished and is quite buggy.


Don't know when that was written, but given it's a man page it could be quite old.

---

### Post by bsmith1051 on 2009-10-30
> **rygle said:**
> Don't know when that was written, but given it's a man page it could be quite old.
Looks like it's from 2005.  Nice catch, though!

---

### Post by giannakp on 2009-10-30
The same problem still exists in 9.10 with kernel 2.6.31-14

---

### Post by imhotep_ on 2009-11-01
i always do this:
```
cd /sys/bus/pci/drivers/ehci_hcd
sudo su
echo -n 0000:00:02.2 > unbind
exit
cd
```you have to ls to see which busses are there
and try out which ones to disable.
works for me :D
(but it's a mayor pita)
you don't by any chance have a 64bit CPU?

---

### Post by lisajo on 2009-11-04
I just have to join this thread; same problem on my side.
 

 Some additional things I figured out:
 
[LIST=1]
[*]Problem occurs when using     mainboard – USB – ports (no matter which); Mainboard has an AMD     SB700 – Chipset providing USB
[*]Switching to USB 1.1 in BIOS     solves issue completely; is a real pain when transferring 1 gig of     data...
[*]Adding a PCI – USB –     controller – card with classic NEC – chipset solves the issue     for the ports on the addon – card. (A pitty that I can't boot from     them using USB...)
[/LIST]
 => is this all kind of a hardware – specific bug?
 Which USB – controller chips are you using?
 

 @ imhotep_: I'm using an 64bit CPU (Athlon X2) but with 32bit Karmic installation. What is the impact of an 64bit CPU?
 Could you perhaps explain your workaround above?
 Do I get this correct, that you just disable port by port and by getting a certain “buggy” one can fix the behavior of the other ports?
 

 ...even if this bug has been around quite a while in Linux, I hope there still is a way working around it without dropping to USB 1.1 – speed...
 

 Have a nice day!
 lisajo

---

### Post by imhotep_ on 2009-11-04
this problem seems to be common among different kinds of 64bit busses.
i had a sb600 bus and now an nvidia3 bus and both errored out as explained
by all here.

"my" workaround was extracted from a different thread somewhere.
it just disables ehci_hcd kicking in @ transfers on the bus.
instead the kernel uses ohci & uchi respectively.

---

### Post by bsmith1051 on 2009-11-04
> **lisajo said:**
> Problem occurs when using     mainboard – USB – ports (no matter which); Mainboard has an AMD     SB700 – Chipset providing USB
Do you have an external USB hub connected?  

P.S. Since my upgrade to 9.10 I haven't had any problems, knock, knock!

---

### Post by lisajo on 2009-11-05
No USB – hub inbetween; direct connection to ports on MB.
 I do have all USB ports free, except the ones I try to connect my USB HDD or stick to. (got some old PS/2 Keyboard and mouse out of my spare box)
 

 Doesn't anyone have an idea what to generally do about this issue?
 I found several similar issues on launchpad – most of them Kernel related and not limited to Ubuntu.
 All of them seemed to go in circles...
 But after some gooling, this behavior does not seem to be too seldom!
 

 Any comments / suggestions?
 Lisa

---

### Post by lisajo on 2009-11-07
I just booted Karmic on an other machine with an AMD SB600 - Chipset providing USB.

...no issues here; full USB 2.0 - support.
(Also with an 64bit CPU Athlon 3000+)

Could I get a feedback of anyone having the USB2.0 - issue on his machine which controller is responsible for USB?

Does anyone have issues with SB600?
Does anyone have no problems with SB700?

...I'd really like to know if this is purly hardware specific or if something else is also kicking in.

Nevertheless, have a nice weekend!
lisajo

---

### Post by giannakp on 2009-11-07
In my system :

```
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)

```

---

### Post by rygle on 2009-11-10
> **imhotep_ said:**
> i always do this:
```
cd /sys/bus/pci/drivers/ehci_hcd
sudo su
echo -n 0000:00:02.2 > unbind
exit
cd
```you have to ls to see which busses are there
and try out which ones to disable.
works for me :D
(but it's a mayor pita)
you don't by any chance have a 64bit CPU?

Thanks imhotep_ for your wisdom, I'll have to give it a try.

I'm using an Acer 5738G laptop with a Core2Duo 2GHz and Centrino 2 chipset, running 32bit Ubuntu 9.04 (haven't upgraded to 9.10 yet as I'm mainly using Windows at present because of this bug, i.e. not by choice). Don't know how wide the system bus is - I would assume 64 bit. Wasn't aware of having these problems with my AMD64 3000+ Nvidia G-Force desktop (running 9.04 32 bit) before it died, which would have also had a 64 bit bus AFAIK.

The laptop is pretty much the same as the specs here;
[http://www.newtechnology.co.in/acer-aspire-5738g-pricespecs/](http://www.newtechnology.co.in/acer-aspire-5738g-pricespecs/)
Except I've got an Nvidia G-105M graphics card built in and only 3Gb of RAM.

I'm running a USB docking station - Targus ACP45AU (identical to ACP45US and ACP45CA as far as I can tell), which connects via USB. I use the docking station for sound, parallel printer, ethernet (built-in to Targus docking station) plus mouse and keyboard (USB from Targus docking station). My external Maxtor drive is plugged directly into the laptop. So effectively I've got two things (HD & dock) plugged directly into the laptop, and then a few things hanging off that.

---

### Post by lisajo on 2009-11-30
I've some news to add on this EHCI – issue...
 

 Couldn't wait to see what's going on with Ubuntu 10.04 (lucid), hoping, that the new kernel in there will sort all this out.
 => I downloaded the daily build live – CD on 2009-11-30, including kernel 2.6.32-5-generic.
 

 The bad news: same, reproducible EHCI – bug, no USB 2.0 support for me. Does only work when disabling USB 2.0 either in BIOS or with the method described above.
 

 I've all the data (dmesg, lspci, lsusb) together;
 I'll try to take the time and file this on launchpad.
 

 ...hoping best for lucid release next year!
 lisajo

---

### Post by nate1010smith on 2009-12-01
I'm having pretty much the same problem. I have a external, powered 500gb maxtor usb hdd and it periodically goes offline and won't reconnect without unplugging it.

I had been using this same drive with 9.04 on the same machine last year and it would never disconnect improperly but I think during that time it was being used to host some shared files and that was preventing the drive from going idle. This is only a guess though, I can't confirm anything about the previous setup.

**lsusb -t [after the failure]:**
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 4: Dev 25, If 0, Class=stor., Driver=usb-storage, 480M

**lsusb -t [after manually reconnecting]:**
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 50, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 4: Dev 25, If 0, Class=stor., Driver=usb-storage, 480M


**from lsusb -v [after failure, only the hub]:**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

**from lsusb -v [after reconnecting, hub and failing device]:**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 050: ID 0d49:7300 Maxtor 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0d49 Maxtor
  idProduct          0x7300 
  bcdDevice            1.21
  iManufacturer           1 
  iProduct                3 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

**/var/log/messages:**
Dec  1 01:10:47 e310 kernel: [1396916.100020] usb 1-2: reset high speed USB device using ehci_hcd and address 45
Dec  1 01:10:47 e310 kernel: [1396916.644016] usb 1-2: reset high speed USB device using ehci_hcd and address 45
Dec  1 01:10:48 e310 kernel: [1396917.188016] usb 1-2: reset high speed USB device using ehci_hcd and address 45
Dec  1 01:10:48 e310 kernel: [1396917.544017] usb 1-2: reset high speed USB device using ehci_hcd and address 45
Dec  1 01:10:48 e310 kernel: [1396917.788046] usb 1-2: USB disconnect, address 45
Dec  1 01:10:48 e310 kernel: [1396917.788671] sd 18:0:0:0: Device offlined - not ready after error recovery
Dec  1 01:10:49 e310 kernel: [1396917.926529] usb 1-2: new high speed USB device using ehci_hcd and address 46
Dec  1 01:10:49 e310 kernel: [1396918.488020] usb 1-2: new high speed USB device using ehci_hcd and address 47
Dec  1 01:10:50 e310 kernel: [1396919.032157] usb 1-2: new high speed USB device using ehci_hcd and address 48
Dec  1 01:10:50 e310 kernel: [1396919.388033] usb 1-2: new high speed USB device using ehci_hcd and address 49
Dec  1 01:10:50 e310 kernel: [1396919.900018] usb 2-2: new full speed USB device using uhci_hcd and address 42
Dec  1 01:10:51 e310 kernel: [1396920.464014] usb 2-2: new full speed USB device using uhci_hcd and address 43
Dec  1 01:10:52 e310 kernel: [1396921.028016] usb 2-2: new full speed USB device using uhci_hcd and address 44
Dec  1 01:10:52 e310 kernel: [1396921.408014] usb 2-2: new full speed USB device using uhci_hcd and address 45

Sorry for the long post, I tried to include anything that might be relevant.

---

### Post by smerral on 2009-12-10
You can also unbind by doing the following:

echo -n 0000:00:**.*4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind

(replacing * with your own module number)

This can be automated to run at boot by entering the command in etc/init.d/rc.local directly below #! /bin/sh

Works for me - hope this helps,

Brian

---

### Post by imhotep_ on 2010-01-07
> **nate1010smith said:**
> 
Sorry for the long post, I tried to include anything that might be relevant.

hint: just use the ubuntu paste service or others
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

as to the bug: confirming it still being present on newest kernel 2.6.32rc3
but i have another suggestion: perhaps it has to do with usb core voltage?
on my usb bus devices which "need" more amperes seem to fail, whereas
small devices like usb sticks work fine. (?)
my core voltage is slightly below 5v (4.9 or something)
perhaps the bus errors out because of this? just a thought ...

---

### Post by nate1010smith on 2010-01-07
> **imhotep_ said:**
> perhaps it has to do with usb core voltage?
on my usb bus devices which "need" more amperes seem to fail, whereas
small devices like usb sticks work fine.

That doesn't seem like it should be causing the problem. This is a desktop computer and should be able to provide far more current than any thing will need, but I guess it could be a possibility. If I get a chance I might check the current draw on the devices I have connected. I have a webcam and a usb stick that don't disconnect. Also, the hdd is powered externally so it should only be using the usb for data.

My guess is still that it has something to do with the drive going idle and then failing to reconnect after. I'm not sure why it wouldn't reconnect though. Maybe too long of a delay while reinitializing? Current draw of the motor while spinning up breaks the data connection?

Whatever the root cause is though, it isn't the biggest issue. Somehow OS X and Windows have dealt with it and don't seem to have any problems with the drive so I would guess that the same solution should be possible on linux.

I think I'll write a script to periodically access files on the drive to prevent it from going idle. That may be a temporary fix and somewhat of a test to see if going idle has anything to do with the disconnect

---

### Post by nate1010smith on 2010-01-23
Update on the idle test. I've been running a script that periodically writes to a file on the external hdd for about 2 weeks now and it has not disconnected once. This has been working as a temporary fix for now but if any one has any ideas of what an actual solution would be I'm willing to help with coding/testing.

---

### Post by skeezer65134 on 2010-01-26
Just thought I'd weigh in here. I'm having a lot of problems with "error: -71" when plugging in external USB hard drives. It's been a pretty consistent problem now for the past couple of weeks. Usually the drives work just fine, with the exception of one of the enclosures I use. All of a sudden today, nothing will load. I did the unbind command as listed above and my drives are back online, but running at super slow USB speeds :(

It really bothers me that ehci is still a problem after all these years. It's a constant problem for people and it would be nice if someone would step up and fix the driver...

I'm running 9.04 x86_64 on a Gigabyte GA-EP45-UD3P board. I have a USB hub, but I am getting these errors both with and without the hub attached.

---

### Post by smerral on 2010-04-27
Well I've been running lucid Beta 2 for a few days now and I'm pleased to say that so far so good. This issue appears to be solved. I would be interested in hearing the experiences of others who may have had this problem in the past.

---

### Post by Luc@Lux on 2010-05-02
Hi, I am having exactly the same issues included in this thread, using 10.04 on an Acer desktop (Aspire E560). It has a Pentium D 2.8 GHz -32 bits-, and the controller is ATI:

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

I connect the mouse/keyboard (Logitech), using a hub. Trying, to connect directly a USB stick gets me to the same error messages.

The same hub, connected to a Mac Mini, works without problems; the Ubuntu installation shares computer/hard disk with Vista 32 bits. In Vista, everything works also fine.

Before Lucid Lynx, the problem happened exactly the same, ehci seems to eventually fail on this computer -I have also installed 10.04 on a separate computer, and it goes smoothly-

---

### Post by Luc@Lux on 2010-05-02
> **Luc@Lux said:**
> Hi, I am having exactly the same issues included in this thread, using 10.04 on an Acer desktop (Aspire E560). It has a Pentium D 2.8 GHz -32 bits-, and the controller is ATI:

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

I connect the mouse/keyboard (Logitech), using a hub. Trying, to connect directly a USB stick gets me to the same error messages.

The same hub, connected to a Mac Mini, works without problems; the Ubuntu installation shares computer/hard disk with Vista 32 bits. In Vista, everything works also fine.

Before Lucid Lynx, the problem happened exactly the same, ehci seems to eventually fail on this computer -I have also installed 10.04 on a separate computer, and it goes smoothly-

I forgot to mention that the problem only happens after putting the system to sleep and then waking it up.

The USB-related part in the /var/log/messages looks like:
[http://paste.ubuntu.com/426755/](http://paste.ubuntu.com/426755/)

---

### Post by mirkob on 2010-09-07
> **smerral said:**
> You can also unbind by doing the following:

echo -n 0000:00:**.*4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind

(replacing * with your own module number)

This can be automated to run at boot by entering the command in etc/init.d/rc.local directly below #! /bin/sh

Works for me - hope this helps,

Brian

Hi 
I have the same problem. Most of the taime my USB sticks or SD card don't work. The only thing that worked was to do the unbind at the command line.
I'd like to do it automatically when I boot but the line above does not seem to work.
If I want to creat a command to do that, how do you do it?
Just put the command in a file and run it like a DOS .bat?
Thanks

---

### Post by mirkob on 2010-09-08
> **mirkob said:**
> Hi 
I have the same problem. Most of the taime my USB sticks or SD card don't work. The only thing that worked was to do the unbind at the command line.
I'd like to do it automatically when I boot but the line above does not seem to work.
If I want to creat a command to do that, how do you do it?
Just put the command in a file and run it like a DOS .bat?
Thanks

Never mind

---

### Post by MttJocy on 2010-12-26
I just wanted to add a note as I found this thread as a result of a similar issue but involving a media player (Philips GoGear).  This is quite a long post to go over the entire solution and it also applies *only* to media players or at least devices with MTP (Media Transfer Protocol) support so media devices anyway, those with other types of device would be best to skip this post I suspect.  This thread was picked up as the error message sequence matches this one at the top of the thread.

> [ 3191.120183] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3201.364268] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3217.612065] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3217.860046] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3228.104204] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[ 3228.237084] scsi 2:0:0:0: Device offlined - not ready after error recovery

I eventually had to find the solution on a foreign language ubuntu site with a lot of patience and some google translate hehe.  As a result I am adding it here so that other English language speakers seeking help with this issue are with any luck going to find it.  Anyway on with the solution :)

The cause in this case is that my device also supports mtp which stops it being registered and mounted as a block device like you might suspect.  To check if this applies to your device (It may well apply to other media players as well as some GoGear devices) make sure you have libmtp8 installed:

```
sudo apt-get install libmtp8
```

Then make sure the device is connected via it's USB connection and run the following command:
```
mtp-detect
```

If you get a very long output that starts out with something like the following:

> libmtp version: 1.0.3

Listing raw device(s)
Device 0 (VID=0471 and PID=084e) is a Philips GoGear SA6014/SA6015/SA6024/SA6025/SA6044/SA6045.
   Found 1 device(s):
   Philips: GoGear SA6014/SA6015/SA6024/SA6025/SA6044/SA6045 (0471:084e) @ bus 2, dev 9
Attempting to connect device(s)

If you don't see the device or you get "No raw devices found" then unfortunately this solution will not work for your device.  On the other hand if you see the device you are looking for in that list then great read on to find out how to access it as an MTP enabled device.

At this point we know the device supports MTP so you need to open a software package that supports MTP devices.  One such example is Rythymbox and it is installed by default in ubuntu.  When you have it open you will either see the device listed in the right hand frame under "Devices" or will have to activate the MTP plugin.  To activate the plugin go to Edit > Plugins then scroll through the list to find "Portable Players - MTP" check the box next to it and hit the close button.

All that done you should now see your device in the right hand side of rythymbox listed under Devices and can drag files over from your media library as needed, any music in your ~/Music directory will automatically have been added to your library but if you have some elsewhere you may need to add it using Music > Import File... for single files or Music > Import Folder... to import entire folders etc.

---

### Post by LxP on 2012-12-17
> **smerral said:**
> You can also unbind by doing the following:

echo -n 0000:00:**.*4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind

(replacing * with your own module number)
I'm experiencing the issue described in this thread on a plug computer running Debian, with an external USB hard drive attached.

Further info on how to determine the "module number" quoted above would be greatly appreciated, as there's nothing similar to that number in my lsusb output.

---

