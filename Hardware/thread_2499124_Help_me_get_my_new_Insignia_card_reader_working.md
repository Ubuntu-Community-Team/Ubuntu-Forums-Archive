---
title: "Help me get my new Insignia card reader working"
date: 2024-07-13
forum: Hardware
---

### Post by sofasurfer on 2024-07-13
New memory card reader Insignia NS-CRSA1.  ```
  Insignia™ - USB 3.0 SD and microSD Memory Card Reader  
```

Older Dell 660 motherboard. ```
   Base Board Information
	Manufacturer: Dell Inc.
	Product Name: 084J0R      
	Version: A00
	Serial Number: .3F0LFX1.CN7016333M02HA.           
	Asset Tag:                       
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0004
	Type: Motherboard
	Contained Object Handles: 0

```

My front ports are black and my rear ports are blue. Worrisome part is that my front ports don't work well. I think they are worn out. 

My new card reader shows nothing in the file browser. Also does not show up under lsubs. ```
  $ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 3151:3020 YICHIP Wireless Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
```

What do you think?

---

### Post by currentshaft on 2024-07-13
Run "sudo dmesg" when you connect the device and see if there are any errors.

---

### Post by sofasurfer on 2024-07-13
I am assuming that I do not need a card inserted into reader to see if the reader is recognized. Please verify this.

Here is the dmesg readout (using the FRONT port) showing only the USB data... ```
 [ 2366.922005] usb 1-1.4: new full-speed USB device number 3 using ehci-pci
[ 2367.001976] usb 1-1.4: device descriptor read/64, error -32
[ 2367.190014] usb 1-1.4: device descriptor read/64, error -32
[ 2367.377979] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[ 2367.457984] usb 1-1.4: device descriptor read/64, error -32
[ 2399.261525] usb 1-1.4: new high-speed USB device number 5 using ehci-pci
[ 2399.374973] usb 1-1.4: New USB device found, idVendor=6655, idProduct=0749, bcdDevice=15.39
[ 2399.374984] usb 1-1.4: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[ 2399.374987] usb 1-1.4: Product: USB3.0 Card Reader
[ 2399.374989] usb 1-1.4: Manufacturer: Generic
[ 2399.374992] usb 1-1.4: SerialNumber: 000000001539
[ 2399.413639] usb-storage 1-1.4:1.0: USB Mass Storage device detected
[ 2399.413808] scsi host8: usb-storage 1-1.4:1.0
[ 2399.413925] usbcore: registered new interface driver usb-storage
[ 2399.423155] usbcore: registered new interface driver uas
[ 2399.863217] usb 1-1.4: USB disconnect, device number 5
[ 7452.265267] perf: interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
[ 8176.765061] usb 1-1.3: new full-speed USB device number 6 using ehci-pci
[ 8176.845043] usb 1-1.3: device descriptor read/64, error -32
[ 8177.033029] usb 1-1.3: device descriptor read/64, error -32
[ 8177.221083] usb 1-1.3: new full-speed USB device number 7 using ehci-pci
[ 8177.301040] usb 1-1.3: device descriptor read/64, error -32
[ 8177.489026] usb 1-1.3: device descriptor read/64, error -32
[ 8177.597275] usb 1-1-port3: attempt power cycle
[ 8178.201037] usb 1-1.3: new full-speed USB device number 8 using ehci-pci
[ 8178.617046] usb 1-1.3: device not accepting address 8, error -32
[ 8178.697047] usb 1-1.3: new full-speed USB device number 9 using ehci-pci
[ 8179.113022] usb 1-1.3: device not accepting address 9, error -32
[ 8179.113255] usb 1-1-port3: unable to enumerate USB device
[ 8553.642897] usb 1-1.3: new full-speed USB device number 10 using ehci-pci
[ 8553.722893] usb 1-1.3: device descriptor read/64, error -32
[ 8554.118891] usb 1-1.3: device descriptor read/64, error -32
[ 8554.306891] usb 1-1.3: new full-speed USB device number 11 using ehci-pci
[ 8554.594871] usb 1-1.3: device descriptor read/64, error -32
[ 8554.782887] usb 1-1.3: device descriptor read/64, error -32
[ 8554.890968] usb 1-1-port3: attempt power cycle
[ 8922.983194] usb 1-1.3: new full-speed USB device number 13 using ehci-pci
[ 8923.275170] usb 1-1.3: device descriptor read/64, error -32
[ 8923.463173] usb 1-1.3: device descriptor read/64, error -32
[ 8923.651182] usb 1-1.3: new full-speed USB device number 14 using ehci-pci
[ 8923.731197] usb 1-1.3: device descriptor read/64, error -32
[ 8923.919168] usb 1-1.3: device descriptor read/64, error -32
[ 8924.027408] usb 1-1-port3: attempt power cycle
[ 8924.631156] usb 1-1.3: new full-speed USB device number 15 using ehci-pci
[ 8925.051135] usb 1-1.3: device not accepting address 15, error -32
[ 8925.131135] usb 1-1.3: new full-speed USB device number 16 using ehci-pci
[ 8925.547138] usb 1-1.3: device not accepting address 16, error -32
[ 8925.547332] usb 1-1-port3: unable to enumerate USB device
 
```

Here is the dmesg readout (using the REAR port) showing only the USB data... ```
 [ 1308.032760] usb 3-1: USB disconnect, device number 2
[ 1317.800577] usb 3-1: new full-speed USB device number 3 using xhci_hcd
[ 1317.972477] usb 3-1: New USB device found, idVendor=3151, idProduct=3020, bcdDevice= 0.02
[ 1317.972486] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1317.972489] usb 3-1: Product: Wireless Device
[ 1317.972492] usb 3-1: Manufacturer: YICHIP
[ 1317.980771] input: YICHIP Wireless Device as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:3151:3020.0007/input/input30
[ 1318.041080] hid-generic 0003:3151:3020.0007: input,hidraw2: USB HID v2.00 Keyboard [YICHIP Wireless Device] on usb-0000:00:14.0-1/input0
[ 1318.057512] input: YICHIP Wireless Device Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/0003:3151:3020.0008/input/input31
[ 1318.116838] input: YICHIP Wireless Device System Control as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/0003:3151:3020.0008/input/input32
[ 1318.117031] input: YICHIP Wireless Device Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/0003:3151:3020.0008/input/input33
[ 1318.117316] hid-generic 0003:3151:3020.0008: input,hiddev1,hidraw3: USB HID v2.00 Mouse [YICHIP Wireless Device] on usb-0000:00:14.0-1/input1
[ 2366.922005] usb 1-1.4: new full-speed USB device number 3 using ehci-pci
[ 2367.001976] usb 1-1.4: device descriptor read/64, error -32
[ 2367.190014] usb 1-1.4: device descriptor read/64, error -32
[ 2367.377979] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[ 2367.457984] usb 1-1.4: device descriptor read/64, error -32
[ 2399.261525] usb 1-1.4: new high-speed USB device number 5 using ehci-pci
[ 2399.374973] usb 1-1.4: New USB device found, idVendor=6655, idProduct=0749, bcdDevice=15.39
[ 2399.374984] usb 1-1.4: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[ 2399.374987] usb 1-1.4: Product: USB3.0 Card Reader
[ 2399.374989] usb 1-1.4: Manufacturer: Generic
[ 2399.374992] usb 1-1.4: SerialNumber: 000000001539
[ 2399.413639] usb-storage 1-1.4:1.0: USB Mass Storage device detected
[ 2399.413808] scsi host8: usb-storage 1-1.4:1.0
[ 2399.413925] usbcore: registered new interface driver usb-storage
[ 2399.423155] usbcore: registered new interface driver uas
[ 2399.863217] usb 1-1.4: USB disconnect, device number 5
[ 7452.265267] perf: interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
[ 8176.765061] usb 1-1.3: new full-speed USB device number 6 using ehci-pci
[ 8176.845043] usb 1-1.3: device descriptor read/64, error -32
[ 8177.033029] usb 1-1.3: device descriptor read/64, error -32
[ 8177.221083] usb 1-1.3: new full-speed USB device number 7 using ehci-pci
[ 8177.301040] usb 1-1.3: device descriptor read/64, error -32
[ 8177.489026] usb 1-1.3: device descriptor read/64, error -32
[ 8177.597275] usb 1-1-port3: attempt power cycle
[ 8178.201037] usb 1-1.3: new full-speed USB device number 8 using ehci-pci
[ 8178.617046] usb 1-1.3: device not accepting address 8, error -32
[ 8178.697047] usb 1-1.3: new full-speed USB device number 9 using ehci-pci
[ 8179.113022] usb 1-1.3: device not accepting address 9, error -32
[ 8179.113255] usb 1-1-port3: unable to enumerate USB device
[ 8553.642897] usb 1-1.3: new full-speed USB device number 10 using ehci-pci
[ 8553.722893] usb 1-1.3: device descriptor read/64, error -32
[ 8554.118891] usb 1-1.3: device descriptor read/64, error -32
[ 8554.306891] usb 1-1.3: new full-speed USB device number 11 using ehci-pci
[ 8554.594871] usb 1-1.3: device descriptor read/64, error -32
[ 8554.782887] usb 1-1.3: device descriptor read/64, error -32
[ 8554.890968] usb 1-1-port3: attempt power cycle  
```

I see that the last few lines of both the FRONT and REAR readouts have errors and they are each different . Obviously a clue to something.

Thanks for the help.

---

### Post by #&amp;thj^% on 2024-07-13
@sofasurfer Dang I hate telling someone any bad news That dongle was uter crap when I tested it recently, they have no mention of Linux anywhere.

But this one will support operating systems	
Windows, MacOS, Android, Linux, iOS.

Found Here: [https://www.amazon.com/Reader-Adapter-Camera-Memory-Wansurs/dp/B0B9QZ4W4Y/ref=pd_ci_mcx_pspc_dp_d_2_t_2?pd_rd_w=rTvTj&content-id=amzn1.sym.568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_p=568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_r=Y0F4K2Q1GKVAK14MN90N&pd_rd_wg=GhSuU&pd_rd_r=1f843957-29a1-4bb4-8aa5-32082b581dbc&pd_rd_i=B0B9QZ4W4Y](https://www.amazon.com/Reader-Adapter-Camera-Memory-Wansurs/dp/B0B9QZ4W4Y/ref=pd_ci_mcx_pspc_dp_d_2_t_2?pd_rd_w=rTvTj&content-id=amzn1.sym.568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_p=568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_r=Y0F4K2Q1GKVAK14MN90N&pd_rd_wg=GhSuU&pd_rd_r=1f843957-29a1-4bb4-8aa5-32082b581dbc&pd_rd_i=B0B9QZ4W4Y)

This is not that device shown below:
```
sudo dmesg|grep Reader
[    4.074635] usb 2-2.2.2.3: Product: USB3.0 Card Reader

```

---

### Post by sofasurfer on 2024-07-13
> **1fallen said:**
> @sofasurfer Dang I hate telling someone any bad news That dongle was uter crap when I tested it recently, they have no mention of Linux anywhere.

But this one will support operating systems	
Windows, MacOS, Android, Linux, iOS.

Fond Here: [https://www.amazon.com/Reader-Adapter-Camera-Memory-Wansurs/dp/B0B9QZ4W4Y/ref=pd_ci_mcx_pspc_dp_d_2_t_2?pd_rd_w=rTvTj&content-id=amzn1.sym.568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_p=568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_r=Y0F4K2Q1GKVAK14MN90N&pd_rd_wg=GhSuU&pd_rd_r=1f843957-29a1-4bb4-8aa5-32082b581dbc&pd_rd_i=B0B9QZ4W4Y](https://www.amazon.com/Reader-Adapter-Camera-Memory-Wansurs/dp/B0B9QZ4W4Y/ref=pd_ci_mcx_pspc_dp_d_2_t_2?pd_rd_w=rTvTj&content-id=amzn1.sym.568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_p=568f3b6b-5aad-4bfd-98ee-d827f03151e4&pf_rd_r=Y0F4K2Q1GKVAK14MN90N&pd_rd_wg=GhSuU&pd_rd_r=1f843957-29a1-4bb4-8aa5-32082b581dbc&pd_rd_i=B0B9QZ4W4Y)

This is not that device shown below:
```
sudo dmesg|grep Reader
[    4.074635] usb 2-2.2.2.3: Product: USB3.0 Card Reader

```


Good to know. If I can not get this one working I will consider ordering one. I really hate ordering on line but a guess you can't beat that price. That is the first one I have seen that says it works with linux. 
 I have been told multiple times that seen though they do not say "linux" that they should still work.

---

### Post by #&amp;thj^% on 2024-07-13
> **sofasurfer said:**
> 
 I have been told multiple times that seen though they do not say "linux" that they should still work.
You will be the first I've seen if you do get it to work.

I tested it on My Samsung TV Android, and various Linux Distros>>>>>Nada...:(

---

