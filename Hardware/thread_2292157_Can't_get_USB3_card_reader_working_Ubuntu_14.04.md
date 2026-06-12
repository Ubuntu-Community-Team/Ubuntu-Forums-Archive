---
title: "Can't get USB3 card reader working Ubuntu 14.04"
date: 2015-08-25
forum: Hardware
---

### Post by derek1234 on 2015-08-25
I have been searching for a solution but have been unable to find anything yet. I have a front panel USB 3.0 card reader model PXR-V301 made by Purex. I can't get it to work with Ubuntu 14.04. It plugs into a blue header on my Gigabyte GA-78LMT-USB3.0 Rev. 5.0 motherboard. It had a picture of a penguin on the box so I mistakenly assumed it would just work with Linux. It also has a USB 3.0 port that seems to be working with my USB 3.0 flash drive, but does not work with my USB 3.0 Seagate external hard drive. The external hard drive only works when plugged into the USB3.0 header on the back of the computer. It also does not recognize any SD cards that I have plugged into it. 
Below is the output of lspci:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 003 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
 No devices plugged into the front card reader show up in 
```
sudo fdisk -l
```
Below is that tail of dmesg. I can't tell if this is normal or not:
```
[   30.865494] usb 9-4: USB disconnect, device number 3
[   40.101261] audit_printk_skb: 93 callbacks suppressed
[   40.101263] type=1400 audit(1440536700.190:43): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2973 comm="apparmor_parser"
[   40.101269] type=1400 audit(1440536700.190:44): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2973 comm="apparmor_parser"
[   40.101614] type=1400 audit(1440536700.194:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2973 comm="apparmor_parser"
[   56.966539] sd 7:0:0:1: Device offlined - not ready after error recovery
[   10.409777] ...........ready
[   56.966703] sd 7:0:0:2: [sdh] READ CAPACITY failed
[   56.966706] sd 7:0:0:2: [sdh]  
[   56.966707] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[   56.966709] sd 7:0:0:2: [sdh] Sense not available.
[   56.966726] sd 7:0:0:2: [sdh] Write Protect is off
[   56.966731] sd 7:0:0:2: [sdh] Mode Sense: 00 06 04 5e
[   56.966745] sd 7:0:0:2: [sdh] Asking for cache data failed
[   56.966747] sd 7:0:0:2: [sdh] Assuming drive cache: write through
[   56.966895] sd 7:0:0:2: [sdh] Attached SCSI removable disk
[   57.210605] usb 9-4: new SuperSpeed USB device number 4 using xhci_hcd
[   57.227273] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[   57.228794] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[   57.228797] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[   57.228798] usb 9-4: Product: USB Storage
[   57.228800] usb 9-4: SerialNumber: 000000000570
[   57.229375] usb-storage 9-4:1.0: USB Mass Storage device detected
[   57.229437] scsi9 : usb-storage 9-4:1.0
[   58.226262] scsi 9:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[   58.226574] scsi 9:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[   58.226880] scsi 9:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[   58.227245] scsi 9:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[   58.227547] scsi 9:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[   58.227742] sd 9:0:0:0: Attached scsi generic sg7 type 0
[   58.227907] sd 9:0:0:1: Attached scsi generic sg8 type 0
[   58.228089] sd 9:0:0:2: Attached scsi generic sg9 type 0
[   58.228274] sd 9:0:0:3: Attached scsi generic sg10 type 0
[   58.228656] sd 9:0:0:4: Attached scsi generic sg11 type 0
[   58.846089] sd 9:0:0:2: [sdh] Spinning up disk...
[   58.958118] usb 9-4: reset SuperSpeed USB device number 4 using xhci_hcd
[   58.974552] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[   58.975361] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205226000
[   58.975364] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205226040
[   58.978541] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[   58.979777] sd 9:0:0:3: [sdi] Attached SCSI removable disk
[   58.980310] sd 9:0:0:4: [sdj] Attached SCSI removable disk
[   58.982559] sd 9:0:0:1: [sdg] Attached SCSI removable disk
[   88.329028] usb 9-4: USB disconnect, device number 4
[  113.838387] sd 9:0:0:2: Device offlined - not ready after error recovery
[   59.976959] ...............ready
[  113.838438] sd 9:0:0:2: rejecting I/O to offline device
[  113.838459] sd 9:0:0:2: rejecting I/O to offline device
[  113.838469] sd 9:0:0:2: rejecting I/O to offline device
[  113.838478] sd 9:0:0:2: [sdh] READ CAPACITY failed
[  113.838482] sd 9:0:0:2: [sdh]  
[  113.838485] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  113.838489] sd 9:0:0:2: [sdh] Sense not available.
[  113.838496] sd 9:0:0:2: rejecting I/O to offline device
[  113.838502] sd 9:0:0:2: [sdh] Write Protect is off
[  113.838506] sd 9:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  113.838513] sd 9:0:0:2: rejecting I/O to offline device
[  113.838518] sd 9:0:0:2: [sdh] Asking for cache data failed
[  113.838522] sd 9:0:0:2: [sdh] Assuming drive cache: write through
[  113.838752] sd 9:0:0:2: [sdh] Attached SCSI removable disk
[  114.086579] usb 9-4: new SuperSpeed USB device number 5 using xhci_hcd
[  114.103169] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  114.104619] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  114.104625] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  114.104630] usb 9-4: Product: USB Storage
[  114.104635] usb 9-4: SerialNumber: 000000000570
[  114.105454] usb-storage 9-4:1.0: USB Mass Storage device detected
[  114.105597] scsi10 : usb-storage 9-4:1.0
[  115.102305] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  115.102672] scsi 10:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  115.103034] scsi 10:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  115.103388] scsi 10:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  115.103747] scsi 10:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  115.104206] sd 10:0:0:0: Attached scsi generic sg7 type 0
[  115.104633] sd 10:0:0:1: Attached scsi generic sg8 type 0
[  115.105332] sd 10:0:0:2: Attached scsi generic sg9 type 0
[  115.106281] sd 10:0:0:3: Attached scsi generic sg10 type 0
[  115.106956] sd 10:0:0:4: Attached scsi generic sg11 type 0
[  115.723575] sd 10:0:0:2: [sdh] Spinning up disk...
[  115.728978] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[  115.729528] sd 10:0:0:1: [sdg] Attached SCSI removable disk
[  115.731324] sd 10:0:0:3: [sdi] Attached SCSI removable disk
[  115.731948] sd 10:0:0:4: [sdj] Attached SCSI removable disk
[  139.563399] usb 9-4: USB disconnect, device number 5
[  164.888743] sd 10:0:0:2: Device offlined - not ready after error recovery
[  116.728978] ............ready
[  164.888790] sd 10:0:0:2: rejecting I/O to offline device
[  164.888807] sd 10:0:0:2: rejecting I/O to offline device
[  164.888817] sd 10:0:0:2: rejecting I/O to offline device
[  164.888826] sd 10:0:0:2: [sdh] READ CAPACITY failed
[  164.888831] sd 10:0:0:2: [sdh]  
[  164.888835] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  164.888840] sd 10:0:0:2: [sdh] Sense not available.
[  164.888849] sd 10:0:0:2: rejecting I/O to offline device
[  164.888856] sd 10:0:0:2: [sdh] Write Protect is off
[  164.888860] sd 10:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  164.888867] sd 10:0:0:2: rejecting I/O to offline device
[  164.888873] sd 10:0:0:2: [sdh] Asking for cache data failed
[  164.888876] sd 10:0:0:2: [sdh] Assuming drive cache: write through
[  164.889113] sd 10:0:0:2: [sdh] Attached SCSI removable disk
[  165.140939] usb 9-4: new SuperSpeed USB device number 6 using xhci_hcd
[  165.157558] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  165.159128] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  165.159136] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  165.159141] usb 9-4: Product: USB Storage
[  165.159145] usb 9-4: SerialNumber: 000000000570
[  165.159815] usb-storage 9-4:1.0: USB Mass Storage device detected
[  165.160000] scsi11 : usb-storage 9-4:1.0
[  166.156564] scsi 11:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  166.156998] scsi 11:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  166.157355] scsi 11:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  166.157712] scsi 11:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  166.158078] scsi 11:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  166.158589] sd 11:0:0:0: Attached scsi generic sg7 type 0
[  166.159202] sd 11:0:0:1: Attached scsi generic sg8 type 0
[  166.160107] sd 11:0:0:2: Attached scsi generic sg9 type 0
[  166.160604] sd 11:0:0:3: Attached scsi generic sg10 type 0
[  166.162465] sd 11:0:0:4: Attached scsi generic sg11 type 0
[  166.778732] sd 11:0:0:2: [sdh] Spinning up disk...
[  166.781693] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[  166.782886] sd 11:0:0:1: [sdg] Attached SCSI removable disk
[  166.785304] sd 11:0:0:3: [sdi] Attached SCSI removable disk
[  166.785933] sd 11:0:0:4: [sdj] Attached SCSI removable disk
[  190.497738] usb 9-4: USB disconnect, device number 6
[  205.624253] systemd-hostnamed[3434]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  215.938996] sd 11:0:0:2: Device offlined - not ready after error recovery
[  167.783280] ............ready
[  215.939044] sd 11:0:0:2: rejecting I/O to offline device
[  215.939062] sd 11:0:0:2: rejecting I/O to offline device
[  215.939071] sd 11:0:0:2: rejecting I/O to offline device
[  215.939077] sd 11:0:0:2: [sdh] READ CAPACITY failed
[  215.939081] sd 11:0:0:2: [sdh]  
[  215.939084] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  215.939088] sd 11:0:0:2: [sdh] Sense not available.
[  215.939094] sd 11:0:0:2: rejecting I/O to offline device
[  215.939101] sd 11:0:0:2: [sdh] Write Protect is off
[  215.939105] sd 11:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  215.939111] sd 11:0:0:2: rejecting I/O to offline device
[  215.939117] sd 11:0:0:2: [sdh] Asking for cache data failed
[  215.939121] sd 11:0:0:2: [sdh] Assuming drive cache: write through
[  215.939354] sd 11:0:0:2: [sdh] Attached SCSI removable disk
[  216.187117] usb 9-4: new SuperSpeed USB device number 7 using xhci_hcd
[  216.203776] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  216.205298] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  216.205306] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  216.205311] usb 9-4: Product: USB Storage
[  216.205315] usb 9-4: SerialNumber: 000000000570
[  216.206043] usb-storage 9-4:1.0: USB Mass Storage device detected
[  216.206230] scsi12 : usb-storage 9-4:1.0
[  217.202340] scsi 12:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  217.202712] scsi 12:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  217.203065] scsi 12:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  217.203418] scsi 12:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  217.203769] scsi 12:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  217.204329] sd 12:0:0:0: Attached scsi generic sg7 type 0
[  217.204806] sd 12:0:0:1: Attached scsi generic sg8 type 0
[  217.205447] sd 12:0:0:2: Attached scsi generic sg9 type 0
[  217.207804] sd 12:0:0:3: Attached scsi generic sg10 type 0
[  217.208363] sd 12:0:0:4: Attached scsi generic sg11 type 0
[  217.824701] sd 12:0:0:2: [sdh] Spinning up disk...
[  217.827501] sd 12:0:0:0: [sdf] Attached SCSI removable disk
[  217.830168] sd 12:0:0:1: [sdg] Attached SCSI removable disk
[  217.831379] sd 12:0:0:3: [sdi] Attached SCSI removable disk
[  217.831997] sd 12:0:0:4: [sdj] Attached SCSI removable disk
[  241.710782] usb 9-4: USB disconnect, device number 7
[  266.827088] sd 12:0:0:2: Device offlined - not ready after error recovery
[  218.828214] ............ready
[  266.827136] sd 12:0:0:2: rejecting I/O to offline device
[  266.827159] sd 12:0:0:2: rejecting I/O to offline device
[  266.827170] sd 12:0:0:2: rejecting I/O to offline device
[  266.827178] sd 12:0:0:2: [sdh] READ CAPACITY failed
[  266.827182] sd 12:0:0:2: [sdh]  
[  266.827185] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  266.827189] sd 12:0:0:2: [sdh] Sense not available.
[  266.827196] sd 12:0:0:2: rejecting I/O to offline device
[  266.827202] sd 12:0:0:2: [sdh] Write Protect is off
[  266.827206] sd 12:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  266.827213] sd 12:0:0:2: rejecting I/O to offline device
[  266.827218] sd 12:0:0:2: [sdh] Asking for cache data failed
[  266.827222] sd 12:0:0:2: [sdh] Assuming drive cache: write through
[  266.827446] sd 12:0:0:2: [sdh] Attached SCSI removable disk
[  267.071089] usb 9-4: new SuperSpeed USB device number 8 using xhci_hcd
[  267.087746] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  267.089303] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  267.089311] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  267.089316] usb 9-4: Product: USB Storage
[  267.089320] usb 9-4: SerialNumber: 000000000570
[  267.089988] usb-storage 9-4:1.0: USB Mass Storage device detected
[  267.090115] scsi13 : usb-storage 9-4:1.0
[  268.086147] scsi 13:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  268.086566] scsi 13:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  268.086921] scsi 13:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  268.087273] scsi 13:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  268.087625] scsi 13:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  268.088063] sd 13:0:0:0: Attached scsi generic sg7 type 0
[  268.088436] sd 13:0:0:1: Attached scsi generic sg8 type 0
[  268.088999] sd 13:0:0:2: Attached scsi generic sg9 type 0
[  268.089766] sd 13:0:0:3: Attached scsi generic sg10 type 0
[  268.093945] sd 13:0:0:4: Attached scsi generic sg11 type 0
[  268.708222] sd 13:0:0:2: [sdh] Spinning up disk...
[  268.712350] sd 13:0:0:0: [sdf] Attached SCSI removable disk
[  268.713594] sd 13:0:0:1: [sdg] Attached SCSI removable disk
[  268.715455] sd 13:0:0:3: [sdi] Attached SCSI removable disk
[  268.716070] sd 13:0:0:4: [sdj] Attached SCSI removable disk
[  292.682737] usb 9-4: USB disconnect, device number 8
[  317.715987] sd 13:0:0:2: Device offlined - not ready after error recovery
[  269.711742] ............ready
[  317.716039] sd 13:0:0:2: rejecting I/O to offline device
[  317.716060] sd 13:0:0:2: rejecting I/O to offline device
[  317.716069] sd 13:0:0:2: rejecting I/O to offline device
[  317.716076] sd 13:0:0:2: [sdh] READ CAPACITY failed
[  317.716079] sd 13:0:0:2: [sdh]  
[  317.716083] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  317.716086] sd 13:0:0:2: [sdh] Sense not available.
[  317.716093] sd 13:0:0:2: rejecting I/O to offline device
[  317.716099] sd 13:0:0:2: [sdh] Write Protect is off
[  317.716104] sd 13:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  317.716110] sd 13:0:0:2: rejecting I/O to offline device
[  317.716116] sd 13:0:0:2: [sdh] Asking for cache data failed
[  317.716119] sd 13:0:0:2: [sdh] Assuming drive cache: write through
[  317.716345] sd 13:0:0:2: [sdh] Attached SCSI removable disk
[  317.959989] usb 9-4: new SuperSpeed USB device number 9 using xhci_hcd
[  317.976669] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  317.978240] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  317.978247] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  317.978252] usb 9-4: Product: USB Storage
[  317.978256] usb 9-4: SerialNumber: 000000000570
[  317.978938] usb-storage 9-4:1.0: USB Mass Storage device detected
[  317.979131] scsi14 : usb-storage 9-4:1.0
[  318.975110] scsi 14:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  318.975494] scsi 14:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  318.975841] scsi 14:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  318.976161] scsi 14:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  318.976470] scsi 14:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  318.976828] sd 14:0:0:0: Attached scsi generic sg7 type 0
[  318.976992] sd 14:0:0:1: Attached scsi generic sg8 type 0
[  318.977157] sd 14:0:0:2: Attached scsi generic sg9 type 0
[  318.977299] sd 14:0:0:3: Attached scsi generic sg10 type 0
[  318.977512] sd 14:0:0:4: Attached scsi generic sg11 type 0
[  319.600405] sd 14:0:0:2: [sdh] Spinning up disk...
[  319.606829] sd 14:0:0:0: [sdf] Attached SCSI removable disk
[  319.607450] sd 14:0:0:1: [sdg] Attached SCSI removable disk
[  319.607988] sd 14:0:0:3: [sdi] Attached SCSI removable disk
[  319.608541] sd 14:0:0:4: [sdj] Attached SCSI removable disk
[  343.620376] usb 9-4: USB disconnect, device number 9
[  368.734097] sd 14:0:0:2: Device offlined - not ready after error recovery
[  320.604654] ............ready
[  368.734144] sd 14:0:0:2: rejecting I/O to offline device
[  368.734161] sd 14:0:0:2: rejecting I/O to offline device
[  368.734171] sd 14:0:0:2: rejecting I/O to offline device
[  368.734181] sd 14:0:0:2: [sdh] READ CAPACITY failed
[  368.734186] sd 14:0:0:2: [sdh]  
[  368.734189] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  368.734194] sd 14:0:0:2: [sdh] Sense not available.
[  368.734202] sd 14:0:0:2: rejecting I/O to offline device
[  368.734209] sd 14:0:0:2: [sdh] Write Protect is off
[  368.734213] sd 14:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  368.734220] sd 14:0:0:2: rejecting I/O to offline device
[  368.734225] sd 14:0:0:2: [sdh] Asking for cache data failed
[  368.734229] sd 14:0:0:2: [sdh] Assuming drive cache: write through
[  368.734485] sd 14:0:0:2: [sdh] Attached SCSI removable disk
[  368.982023] usb 9-4: new SuperSpeed USB device number 10 using xhci_hcd
[  368.998651] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  369.000197] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  369.000203] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  369.000206] usb 9-4: Product: USB Storage
[  369.000209] usb 9-4: SerialNumber: 000000000570
[  369.000791] usb-storage 9-4:1.0: USB Mass Storage device detected
[  369.000919] scsi15 : usb-storage 9-4:1.0
[  369.997232] scsi 15:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  369.997546] scsi 15:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  369.997846] scsi 15:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  369.998209] scsi 15:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  369.998519] scsi 15:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  369.999032] sd 15:0:0:0: Attached scsi generic sg7 type 0
[  369.999483] sd 15:0:0:1: Attached scsi generic sg8 type 0
[  370.000166] sd 15:0:0:2: Attached scsi generic sg9 type 0
[  370.000674] sd 15:0:0:3: Attached scsi generic sg10 type 0
[  370.001031] sd 15:0:0:4: Attached scsi generic sg11 type 0
[  370.414144] sd 15:0:0:3: [sdi] Attached SCSI removable disk
[  370.619177] sd 15:0:0:2: [sdh] Spinning up disk...
[  370.623361] sd 15:0:0:0: [sdf] Attached SCSI removable disk
[  370.625778] sd 15:0:0:1: [sdg] Attached SCSI removable disk
[  370.626956] sd 15:0:0:4: [sdj] Attached SCSI removable disk
[  394.255461] usb 9-4: USB disconnect, device number 10
[  419.625466] sd 15:0:0:2: Device offlined - not ready after error recovery
[  371.622897] ............ready
[  419.625509] sd 15:0:0:2: rejecting I/O to offline device
[  419.625525] sd 15:0:0:2: rejecting I/O to offline device
[  419.625534] sd 15:0:0:2: rejecting I/O to offline device
[  419.625540] sd 15:0:0:2: [sdh] READ CAPACITY failed
[  419.625544] sd 15:0:0:2: [sdh]  
[  419.625547] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  419.625551] sd 15:0:0:2: [sdh] Sense not available.
[  419.625558] sd 15:0:0:2: rejecting I/O to offline device
[  419.625564] sd 15:0:0:2: [sdh] Write Protect is off
[  419.625568] sd 15:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  419.625574] sd 15:0:0:2: rejecting I/O to offline device
[  419.625580] sd 15:0:0:2: [sdh] Asking for cache data failed
[  419.625584] sd 15:0:0:2: [sdh] Assuming drive cache: write through
[  419.625815] sd 15:0:0:2: [sdh] Attached SCSI removable disk
[  419.873529] usb 9-4: new SuperSpeed USB device number 11 using xhci_hcd
[  419.890112] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  419.891661] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  419.891668] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  419.891673] usb 9-4: Product: USB Storage
[  419.891678] usb 9-4: SerialNumber: 000000000570
[  419.892341] usb-storage 9-4:1.0: USB Mass Storage device detected
[  419.892566] scsi16 : usb-storage 9-4:1.0
[  420.888679] scsi 16:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  420.889103] scsi 16:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  420.889467] scsi 16:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  420.889829] scsi 16:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  420.890184] scsi 16:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  420.890600] sd 16:0:0:0: Attached scsi generic sg7 type 0
[  420.891109] sd 16:0:0:1: Attached scsi generic sg8 type 0
[  420.892183] sd 16:0:0:2: Attached scsi generic sg9 type 0
[  420.892677] sd 16:0:0:3: Attached scsi generic sg10 type 0
[  420.893040] sd 16:0:0:4: Attached scsi generic sg11 type 0
[  421.510258] sd 16:0:0:2: [sdh] Spinning up disk...
[  421.513806] sd 16:0:0:0: [sdf] Attached SCSI removable disk
[  421.515499] sd 16:0:0:1: [sdg] Attached SCSI removable disk
[  421.517203] sd 16:0:0:3: [sdi] Attached SCSI removable disk
[  421.517817] sd 16:0:0:4: [sdj] Attached SCSI removable disk
[  445.638889] usb 9-4: USB disconnect, device number 11
[  470.645662] sd 16:0:0:2: Device offlined - not ready after error recovery
[  422.514335] ............ready
[  470.645710] sd 16:0:0:2: rejecting I/O to offline device
[  470.645727] sd 16:0:0:2: rejecting I/O to offline device
[  470.645736] sd 16:0:0:2: rejecting I/O to offline device
[  470.645746] sd 16:0:0:2: [sdh] READ CAPACITY failed
[  470.645751] sd 16:0:0:2: [sdh]  
[  470.645755] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  470.645759] sd 16:0:0:2: [sdh] Sense not available.
[  470.645768] sd 16:0:0:2: rejecting I/O to offline device
[  470.645775] sd 16:0:0:2: [sdh] Write Protect is off
[  470.645780] sd 16:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  470.645786] sd 16:0:0:2: rejecting I/O to offline device
[  470.645792] sd 16:0:0:2: [sdh] Asking for cache data failed
[  470.645796] sd 16:0:0:2: [sdh] Assuming drive cache: write through
[  470.646019] sd 16:0:0:2: [sdh] Attached SCSI removable disk
[  470.897699] usb 9-4: new SuperSpeed USB device number 12 using xhci_hcd
[  470.914278] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
[  470.915831] usb 9-4: New USB device found, idVendor=05e3, idProduct=0732
[  470.915838] usb 9-4: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[  470.915843] usb 9-4: Product: USB Storage
[  470.915847] usb 9-4: SerialNumber: 000000000570
[  470.916521] usb-storage 9-4:1.0: USB Mass Storage device detected
[  470.916705] scsi17 : usb-storage 9-4:1.0
[  471.912866] scsi 17:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  471.913232] scsi 17:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  471.913649] scsi 17:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  471.914130] scsi 17:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  471.914544] scsi 17:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0570 PQ: 0 ANSI: 6
[  471.914979] sd 17:0:0:0: Attached scsi generic sg7 type 0
[  471.915433] sd 17:0:0:1: Attached scsi generic sg8 type 0
[  471.916327] sd 17:0:0:2: Attached scsi generic sg9 type 0
[  471.917737] sd 17:0:0:3: Attached scsi generic sg10 type 0
[  471.918237] sd 17:0:0:4: Attached scsi generic sg11 type 0
[  472.536536] sd 17:0:0:2: [sdh] Spinning up disk...
[  472.540044] sd 17:0:0:0: [sdf] Attached SCSI removable disk
[  472.541209] sd 17:0:0:1: [sdg] Attached SCSI removable disk
[  472.543019] sd 17:0:0:3: [sdi] Attached SCSI removable disk
[  472.543640] sd 17:0:0:4: [sdj] Attached SCSI removable disk
[  526.645368] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[  531.844201] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[  532.047999] usb 9-4: device not accepting address 12, error -62
[  536.031987] hub 9-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  538.589547] hub 9-0:1.0: Could not disable port 4 after 2000 ms
[  543.752440] xhci_hcd 0000:02:00.0: Timeout while waiting for reset device command
[  548.747498] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[  553.946428] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[  554.150229] usb 9-4: device not accepting address 12, error -62
[  558.134512] hub 9-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  560.692068] hub 9-0:1.0: Could not disable port 4 after 2000 ms
[  560.692241] usb 9-4: USB disconnect, device number 12
[  560.692399] sd 17:0:0:2: Device offlined - not ready after error recovery
[  473.538519] ............ready
[  560.692452] sd 17:0:0:2: rejecting I/O to offline device
[  560.692470] sd 17:0:0:2: rejecting I/O to offline device
[  560.692482] sd 17:0:0:2: rejecting I/O to offline device
[  560.692496] sd 17:0:0:2: [sdh] READ CAPACITY failed
[  560.692502] sd 17:0:0:2: [sdh]  
[  560.692509] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  560.692517] sd 17:0:0:2: [sdh] Sense not available.
[  560.692532] sd 17:0:0:2: rejecting I/O to offline device
[  560.692541] sd 17:0:0:2: [sdh] Write Protect is off
[  560.692550] sd 17:0:0:2: [sdh] Mode Sense: 00 00 00 00
[  560.692557] sd 17:0:0:2: rejecting I/O to offline device
[  560.692565] sd 17:0:0:2: [sdh] Asking for cache data failed
[  560.692570] sd 17:0:0:2: [sdh] Assuming drive cache: write through
[  560.692796] sd 17:0:0:2: [sdh] Attached SCSI removable disk
[  560.703157] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880095fa7000
[  560.703164] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880095fa7040
[ 1622.897119] sdk: detected capacity change from 7751073792 to 0
[ 1675.595727] usb 8-1.3: USB disconnect, device number 3
[ 1680.592301] xhci_hcd 0000:02:00.0: Timeout while waiting for configure endpoint command
[ 1685.723487] xhci_hcd 0000:02:00.0: xHCI host not responding to stop endpoint command.
[ 1685.723495] xhci_hcd 0000:02:00.0: Assuming host is dying, halting host.
[ 1685.723524] xhci_hcd 0000:02:00.0: HC died; cleaning up
[ 1685.723555] usb 8-1: USB disconnect, device number 2
[ 1685.724008] usb 9-2: USB disconnect, device number 2
```

It works under windows. I also noticed that when I log in it takes a lot longer when this device is plugged in. It has a red power light on the front, and it will stay lit until shortly after I log in. 

Any help in getting this working would be greatly appreciated!
Thanks,
Derek

---

### Post by howefield on 2015-08-26
Usually after plugging the drive, pulling off the last 35 lines in dmesg would be sufficient rather than the 402 that you provided.

There are a lot of...
```
[  114.103169] usb 9-4: Parent hub missing LPM exit latency info.  Power management will be impacted.
```
in your dmesg, perhaps it is related, you might browse this [thread ]("http://askubuntu.com/questions/210879/external-usb-3-drive-not-recognized") whilst you wait for someone to come along with a better idea of what is wrong.

Not a huge help but take the USB ID, append ubuntu and search with your favourite search engine. 

Does it work if you plug it into a USB 2 header ?

---

