---
title: "Asus Zenbook UX303 - SDXC Card Reader not resuming from suspend"
date: 2016-06-22
forum: Hardware
---

### Post by Niels_M. on 2016-06-22
Dear Forum,

i run Ubuntu 16.04 on an ASUS Zenbook UX303 LN. Everything is working fine so far. The SDXC-Card Reader runs well and good after a fresh boot.
However, once i go into suspend and resume the machine, the card reader will not come back up. Removing and re-inserting the actual card in it does nothing. 
This happens with TLP or Laptop-Mode-Tools installed and also with both of them absent. 

I suspect that the reader is somehow internally connected to the USB. Here's an lsusb before suspending 
```
$ lsusb
Bus 002 Device 004: ID 05e3:0747 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 064e:9700 Suyin Corp. Asus Integrated Webcam
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0b95:7e2b ASIX Electronics Corp. AX88772B
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
and heres one after resuming
```
$ lsusb
Bus 002 Device 004: ID 05e3:0747 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 064e:9700 Suyin Corp. Asus Integrated Webcam
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0b95:7e2b ASIX Electronics Corp. AX88772B
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Note the change in the first row.
Also, here's a dmesg from the suspend/resume time, i will mark some interesing lines bold (CIFS is needed for the exfat filesystem on the SDXC card)

```
[  575.851571] PM: Syncing filesystems ... done.
[  575.858861] PM: Preparing system for sleep (mem)
[  575.859179] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  575.861053] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  575.862198] PM: Suspending system (mem)
[  575.862211] Suspending console(s) (use no_console_suspend to debug)
[  575.862578] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  575.863759] sd 0:0:0:0: [sda] Stopping disk
[  575.935644] PM: suspend of devices complete after 73.287 msecs
[  575.955520] PM: late suspend of devices complete after 19.875 msecs
[  575.956051] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  575.971601] PM: noirq suspend of devices complete after 16.079 msecs
[  575.971875] ACPI: Preparing to enter system sleep state S3
[  575.982562] ACPI : EC: EC stopped
[  575.982562] PM: Saving platform NVS memory
[  575.982593] Disabling non-boot CPUs ...
[  575.982777] Broke affinity for irq 46
[  575.983802] smpboot: CPU 1 is now offline
[  575.999944] Broke affinity for irq 42
[  575.999947] Broke affinity for irq 44
[  575.999951] Broke affinity for irq 46
[  575.999953] Broke affinity for irq 47
[  576.000969] smpboot: CPU 2 is now offline
[  576.011866] Broke affinity for irq 1
[  576.011868] Broke affinity for irq 8
[  576.011869] Broke affinity for irq 9
[  576.011871] Broke affinity for irq 12
[  576.011873] Broke affinity for irq 42
[  576.011875] Broke affinity for irq 43
[  576.011876] Broke affinity for irq 44
[  576.011878] Broke affinity for irq 45
[  576.011880] Broke affinity for irq 46
[  576.011882] Broke affinity for irq 47
[  576.011884] Broke affinity for irq 50
[  576.012896] smpboot: CPU 3 is now offline
[  576.025133] ACPI: Low-level resume complete
[  576.025186] ACPI : EC: EC started
[  576.025187] PM: Restoring platform NVS memory
[  576.027168] microcode: CPU0 microcode updated early to revision 0x22, date = 2015-09-11
[  576.027193] Enabling non-boot CPUs ...
[  576.045417] x86: Booting SMP configuration:
[  576.045418] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  576.046659] microcode: CPU1 microcode updated early to revision 0x22, date = 2015-09-11
[  576.049814]  cache: parent cpu1 should not be sleeping
[  576.049932] CPU1 is up
[  576.069456] smpboot: Booting Node 0 Processor 2 APIC 0x1
[  576.072991]  cache: parent cpu2 should not be sleeping
[  576.073111] CPU2 is up
[  576.089486] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  576.093065]  cache: parent cpu3 should not be sleeping
[  576.093142] CPU3 is up
[  576.096708] ACPI: Waking up from system sleep state S3
**[  576.147136] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI**
[  576.161531] PM: noirq resume of devices complete after 14.520 msecs
[  576.167451] PM: early resume of devices complete after 5.906 msecs
[  576.168755] rtc_cmos 00:04: System wakeup disabled by ACPI
[  576.169772] sd 0:0:0:0: [sda] Starting disk
[  576.204405] xhci_hcd 0000:00:14.0: port 7 resume PLC timeout
**[  576.276370] usb 2-4: usb_reset_and_verify_device Failed to disable LTM**
               .
[  576.433459] usb 1-5: reset high-speed USB device number 4 using xhci_hcd
[  576.485338] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  576.488145] ata1.00: configured for UDMA/133
[  576.501291] ahci 0000:00:1f.2: port does not support device sleep
[  576.729554] usb 1-8: reset full-speed USB device number 6 using xhci_hcd
[  576.859778] PM: resume of devices complete after 692.350 msecs
[  576.860262] PM: Finishing wakeup.
[  576.860263] Restarting tasks ... done.
[  576.880574] Bluetooth: hci0: read Intel version: 370810011002270d00
[  576.883669] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.2.27.d.bseq
[  576.996462] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  576.996564] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[  576.996726] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[  577.054318] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[  577.054474] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[  577.065131] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  577.065924] IPv6: ADDRCONF(NETDEV_UP): enx9cebe81a9bed: link is not ready
[  577.066428] asix 1-3.2:1.0 enx9cebe81a9bed: link down
[  577.066776] IPv6: ADDRCONF(NETDEV_UP): enx9cebe81a9bed: link is not ready
[  577.093561] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[  577.129131] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  577.137364] usb 2-3: new SuperSpeed USB device number 5 using xhci_hcd
[  577.156184] usb 2-3: New USB device found, idVendor=05e3, idProduct=0616
[  577.156188] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  577.156189] usb 2-3: Product: USB3.0 Hub
[  577.156190] usb 2-3: Manufacturer: GenesysLogic
[  577.158699] hub 2-3:1.0: USB hub found
[  577.158989] hub 2-3:1.0: 4 ports detected
**[  577.161087] usb 2-4: USB disconnect, device number 4**
**[  605.610566] CIFS VFS: Error connecting to socket. Aborting operation.**
**[  605.610623] CIFS VFS: cifs_mount failed w/return code = -101**
[  650.963576] usb 1-3: USB disconnect, device number 3
[  650.963579] usb 1-3.2: USB disconnect, device number 5
[  650.963668] asix 1-3.2:1.0 enx9cebe81a9bed: unregister 'asix' usb-0000:00:14.0-3.2, ASIX AX88772 USB 2.0 Ethernet
[  650.975288] usb 1-3.4: USB disconnect, device number 7
[  650.990253] usb 2-3: USB disconnect, device number 5
[  652.510767] usb 2-2: new SuperSpeed USB device number 6 using xhci_hcd
[  652.530443] usb 2-2: New USB device found, idVendor=05e3, idProduct=0616
[  652.530445] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  652.530447] usb 2-2: Product: USB3.0 Hub
[  652.530448] usb 2-2: Manufacturer: GenesysLogic
[  652.532543] hub 2-2:1.0: USB hub found
[  652.532859] hub 2-2:1.0: 4 ports detected
[  652.574575] usb 1-2: new high-speed USB device number 8 using xhci_hcd
[  652.734155] usb 1-2: New USB device found, idVendor=05e3, idProduct=0610
[  652.734157] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  652.734159] usb 1-2: Product: USB2.0 Hub
[  652.734160] usb 1-2: Manufacturer: GenesysLogic
[  652.738393] hub 1-2:1.0: USB hub found
[  652.742570] hub 1-2:1.0: 4 ports detected
[  653.074621] usb 1-2.2: new high-speed USB device number 9 using xhci_hcd
[  653.193228] usb 1-2.2: New USB device found, idVendor=0b95, idProduct=7e2b
[  653.193231] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  653.193233] usb 1-2.2: SerialNumber: 00228F
[  653.987958] asix 1-2.2:1.0 eth0: register 'asix' at usb-0000:00:14.0-2.2, ASIX AX88772 USB 2.0 Ethernet, 9c:eb:e8:1a:9b:ed
[  654.070588] usb 1-2.4: new full-speed USB device number 10 using xhci_hcd
[  654.166105] usb 1-2.4: New USB device found, idVendor=046d, idProduct=c52b
[  654.166107] usb 1-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  654.166109] usb 1-2.4: Product: USB Receiver
[  654.166110] usb 1-2.4: Manufacturer: Logitech
[  654.171980] logitech-djreceiver 0003:046D:C52B.0008: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2.4/input2
[  654.291590] input: Logitech Performance MX as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.2/0003:046D:C52B.0008/0003:046D:101A.0009/input/input29
[  654.291749] logitech-hidpp-device 0003:046D:101A.0009: input,hidraw1: USB HID v1.11 Mouse [Logitech Performance MX] on usb-0000:00:14.0-2.4:1
[  654.295681] input: Logitech K750 as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.2/0003:046D:C52B.0008/0003:046D:4002.000A/input/input30
[  654.296054] logitech-hidpp-device 0003:046D:4002.000A: input,hidraw2: USB HID v1.11 Keyboard [Logitech K750] on usb-0000:00:14.0-2.4:2
[  655.833474] asix 1-2.2:1.0 enx9cebe81a9bed: renamed from eth0
[  655.856221] IPv6: ADDRCONF(NETDEV_UP): enx9cebe81a9bed: link is not ready
[  655.857077] asix 1-2.2:1.0 enx9cebe81a9bed: link up, 100Mbps, full-duplex, lpa 0xCDE1
[  656.038070] asix 1-2.2:1.0 enx9cebe81a9bed: link up, 100Mbps, full-duplex, lpa 0xCDE1


```



Does anyone have any idea how to fix this? As i use the card reader a lot, this is super annoying to me... Thank you a lot in advance.

---

### Post by QDR06VV9 on 2016-06-22
Hi Niels_M. Welcome to the Forums and being that you are new here I have edited your post using "code tags" makes it a bit easier to read and to help you. To Learn how to use Code tags see my signature.
Kind Regards and Good Luck

---

### Post by Niels_M. on 2016-06-22
Thanks for your changes. 
[FONT=arial]One more add: By fiddling with the SD-Card, i am now 100% sure that the[SIZE=1] USB [SIZE=2]Device 05e3:0747 is the reader in question. When the machine has not been suspended i appears and disappears just fine on inserting/taking out the SD card. One suspend however, and it's gone for good. Suggestions?[/SIZE][/SIZE][/FONT]

---

### Post by QDR06VV9 on 2016-06-22
It is worth a try... if you have another USB Card Reader to check with.
Been mentioned a few times that SDXC cards when used with other readers work as expected.
[http://ubuntuforums.org/showthread.php?t=2322928](http://ubuntuforums.org/showthread.php?t=2322928)  For just one example.
> ***I purchased a six dollar external card reader from Amazon, plugged  the reader into one of the USB3 slots and I can now read the SDXXC  cards.***  I hope this info helps others.
Or maybe this will get the thread rolling for you.
My small bit to help.

---

### Post by Niels_M. on 2016-06-23
Hello everyone, just letting you know i was able to solve this by using acpitool.
Using 
```

acpitool -W

``` 
i have enabled all responsible controllers (including pci-e) so they can wake up the system from suspend. This fixed the issue with the SD Card slot not coming back after suspend, it's coming up nice and fine now. I suspect the problem was one of the controllers entering a powerstate it could not wake up the SD card slot from anymore.

---

### Post by QDR06VV9 on 2016-06-23
Nice Work!:D Glad you got it sorted out.
Now if you would mark your thread as solved, To help other visitors with similar problem. 
Thanks and Regards

---

### Post by Niels_M. on 2016-06-23
I think i already did that right after my post, didn't i? It looks like solved on my end.

---

### Post by QDR06VV9 on 2016-06-23
Yep! it took a bit longer on my end I guess.;)
And Thanks Again!

---

