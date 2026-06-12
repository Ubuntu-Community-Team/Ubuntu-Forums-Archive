---
title: "Dell WD19 dock Realtek 8153 problem on reconnect"
date: 2021-02-06
forum: Hardware
---

### Post by thanosz01 on 2021-02-06
I have a Dell WD19 dock (**no **thunderbolt, just USB3.1) which I connect to a Dell Latidute 7400. I boot Ubuntu and everything works. When disconnecting and reconnecting, the network adapter of the dock does not work. All other USB devices and the external display work, it is just the ethernet adatper that does not work. The only thing that saves the day is to reload xhci_pci module (modprobe -r xhci_pci  && modprobe xhci_pci)

What is driving me crazy is that booting opensuse Tumbleweed I do not see this problem. The ethernet adapter of the dock works no matter how many disconnects/reconnects I attempt. I even booted Ubuntu off the Tumbleweed kernel and still have the same the problem on Ubuntu so I am really puzzled about what might be wrong here. If it is not the kernel, then what might be interfering? Why on another distrto this works beats the hell out of me

Here is some more detailed info

On first boot
# lsusb         [B]
Bus 004 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter[/B]
Bus 004 Device 003: ID 0bda:0413 Realtek Semiconductor Corp. 
Bus 004 Device 002: ID 0bda:0487 Realtek Semiconductor Corp. Dell dock
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0781:5583 SanDisk Corp. Ultra Fit
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0a5c:5843 Broadcom Corp. 58200
Bus 001 Device 003: ID 1bcf:28c4 Sunplus Innovation Technology Inc. Integrated_Webcam_HD
Bus 001 Device 008: ID 8087:0aaa Intel Corp. 
Bus 001 Device 006: ID 413c:b06e Dell Computer Corp. 
Bus 001 Device 012: ID 413c:b06f Dell Computer Corp. 
Bus 001 Device 010: ID 0bda:402e Realtek Semiconductor Corp. 
Bus 001 Device 013: ID 045e:0779 Microsoft Corp. LifeCam HD-3000
Bus 001 Device 011: ID 0b0e:0313 GN Netcom 
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 007: ID 1f4d:c803 G-Tek Electronics Group 
Bus 001 Device 004: ID 0bda:5413 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:5487 Realtek Semiconductor Corp. Dell dock
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Disconnecting
Feb  6 16:38:22 CQ2WL13 kernel: [   85.688614] usb 1-1: USB disconnect, device number 2
Feb  6 16:38:22 CQ2WL13 kernel: [   85.688657] usb 1-1.3: USB disconnect, device number 4
Feb  6 16:38:22 CQ2WL13 kernel: [   85.688662] usb 1-1.3.2: USB disconnect, device number 7
Feb  6 16:38:23 CQ2WL13 kernel: [   85.755838] dvb_usb_v2: 'Trekstor DVB-T Stick Terres 2.0:1-1.3.2' successfully deinitialized and disconnected
Feb  6 16:38:23 CQ2WL13 kernel: [   85.757396] usb 1-1.3.3: USB disconnect, device number 9
Feb  6 16:38:23 CQ2WL13 kernel: [   85.757414] usb 1-1.3.3.2: USB disconnect, device number 11
Feb  6 16:38:23 CQ2WL13 kernel: [   85.766231] r8152 4-1.4:1.0 enx3448eda91d0a: Stop submitting intr, status -71
Feb  6 16:38:23 CQ2WL13 kernel: [   85.845701] usb 1-1.3.3.3: USB disconnect, device number 13
Feb  6 16:38:23 CQ2WL13 kernel: [   85.911772] usb 1-1.3.4: USB disconnect, device number 10
Feb  6 16:38:23 CQ2WL13 kernel: [   85.915614] usb 1-1.3.5: USB disconnect, device number 12
Feb  6 16:38:23 CQ2WL13 kernel: [   85.920281] usb 1-1.5: USB disconnect, device number 6
Feb  6 16:38:25 CQ2WL13 kernel: [   87.973825] r8152 4-1.4:1.0 enx3448eda91d0a: Tx status -71
Feb  6 16:38:26 CQ2WL13 kernel: [   88.965818] r8152 4-1.4:1.0 enx3448eda91d0a: Tx status -71
Feb  6 16:38:27 CQ2WL13 kernel: [   89.818877] **usb usb4-port1: Cannot enable. Maybe the USB cable is bad?**
Feb  6 16:38:27 CQ2WL13 kernel: [   89.821999] usb 4-1: USB disconnect, device number 2
Feb  6 16:38:27 CQ2WL13 kernel: [   89.822001] usb 4-1.3: USB disconnect, device number 3
Feb  6 16:38:27 CQ2WL13 kernel: [   89.822615] usb 4-1.4: USB disconnect, device number 4


Reconnecting
Feb  6 16:38:37 CQ2WL13 kernel: [  100.644787] usb 1-1: new high-speed USB device number 14 using xhci_hcd
Feb  6 16:38:38 CQ2WL13 kernel: [  100.797390] usb 1-1: New USB device found, idVendor=0bda, idProduct=5487, bcdDevice= 1.47
Feb  6 16:38:38 CQ2WL13 kernel: [  100.797396] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  6 16:38:38 CQ2WL13 kernel: [  100.797400] usb 1-1: Product: Dell dock
Feb  6 16:38:38 CQ2WL13 kernel: [  100.797403] usb 1-1: Manufacturer: Dell Inc.
Feb  6 16:38:38 CQ2WL13 kernel: [  100.798627] hub 1-1:1.0: USB hub found
Feb  6 16:38:38 CQ2WL13 kernel: [  100.798877] hub 1-1:1.0: 5 ports detected
Feb  6 16:38:38 CQ2WL13 kernel: [  101.084455] usb 1-1.3: new high-speed USB device number 15 using xhci_hcd
Feb  6 16:38:38 CQ2WL13 kernel: [  101.198363] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=5413, bcdDevice= 1.21
Feb  6 16:38:38 CQ2WL13 kernel: [  101.198364] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  6 16:38:38 CQ2WL13 kernel: [  101.198381] usb 1-1.3: Product: Dell dock
Feb  6 16:38:38 CQ2WL13 kernel: [  101.198381] usb 1-1.3: Manufacturer: Dell Inc.
Feb  6 16:38:38 CQ2WL13 kernel: [  101.199633] hub 1-1.3:1.0: USB hub found
Feb  6 16:38:38 CQ2WL13 kernel: [  101.200788] hub 1-1.3:1.0: 6 ports detected
Feb  6 16:38:38 CQ2WL13 kernel: [  101.284406] usb 1-1.5: new high-speed USB device number 16 using xhci_hcd
Feb  6 16:38:38 CQ2WL13 kernel: [  101.390141] usb 1-1.5: New USB device found, idVendor=413c, idProduct=b06e, bcdDevice= 1.01
Feb  6 16:38:38 CQ2WL13 kernel: [  101.390142] usb 1-1.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb  6 16:38:38 CQ2WL13 kernel: [  101.390143] usb 1-1.5: Product: Dell dock
Feb  6 16:38:38 CQ2WL13 kernel: [  101.391446] hid-generic 0003:413C:B06E.0005: hiddev0,hidraw1: USB HID v1.11 Device [Dell dock] on usb-0000:00:14.0-1.5/input0
Feb  6 16:38:38 CQ2WL13 kernel: [  101.504333] usb 1-1.3.2: new high-speed USB device number 17 using xhci_hcd
Feb  6 16:38:38 CQ2WL13 kernel: [  101.624115] usb 1-1.3.2: New USB device found, idVendor=1f4d, idProduct=c803, bcdDevice= 1.00
Feb  6 16:38:38 CQ2WL13 kernel: [  101.624117] usb 1-1.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb  6 16:38:38 CQ2WL13 kernel: [  101.624118] usb 1-1.3.2: Product: RTL2838UHIDIR
Feb  6 16:38:38 CQ2WL13 kernel: [  101.624118] usb 1-1.3.2: Manufacturer: Realtek
Feb  6 16:38:38 CQ2WL13 kernel: [  101.624119] usb 1-1.3.2: SerialNumber: 00000001
Feb  6 16:38:38 CQ2WL13 kernel: [  101.631553] usb 1-1.3.2: dvb_usb_v2: found a 'Trekstor DVB-T Stick Terres 2.0' in warm state
Feb  6 16:38:38 CQ2WL13 kernel: [  101.662534] usb 1-1.3.2: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
Feb  6 16:38:38 CQ2WL13 kernel: [  101.662538] dvbdev: DVB: registering new adapter (Trekstor DVB-T Stick Terres 2.0)
Feb  6 16:38:38 CQ2WL13 kernel: [  101.662540] usb 1-1.3.2: media controller created
Feb  6 16:38:38 CQ2WL13 kernel: [  101.662777] dvbdev: dvb_create_media_entity: media entity 'dvb-demux' registered.
Feb  6 16:38:38 CQ2WL13 kernel: [  101.664102] i2c i2c-13: Added multiplexed i2c bus 14
Feb  6 16:38:38 CQ2WL13 kernel: [  101.664104] rtl2832 13-0010: Realtek RTL2832 successfully attached
Feb  6 16:38:38 CQ2WL13 kernel: [  101.664118] usb 1-1.3.2: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
Feb  6 16:38:38 CQ2WL13 kernel: [  101.664121] dvbdev: dvb_create_media_entity: media entity 'Realtek RTL2832 (DVB-T)' registered.
Feb  6 16:38:38 CQ2WL13 kernel: [  101.664182] fc0013: Fitipower FC0013 successfully attached.
Feb  6 16:38:38 CQ2WL13 kernel: [  101.665502] rtl2832_sdr rtl2832_sdr.1.auto: Registered as swradio0
Feb  6 16:38:38 CQ2WL13 kernel: [  101.665503] rtl2832_sdr rtl2832_sdr.1.auto: Realtek RTL2832 SDR attached
Feb  6 16:38:38 CQ2WL13 kernel: [  101.665503] rtl2832_sdr rtl2832_sdr.1.auto: SDR API is still slightly experimental and functionality changes may follow
Feb  6 16:38:38 CQ2WL13 kernel: [  101.672044] Registered IR keymap rc-empty
Feb  6 16:38:38 CQ2WL13 kernel: [  101.672061] rc rc0: Trekstor DVB-T Stick Terres 2.0 as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3.2/rc/rc0
Feb  6 16:38:38 CQ2WL13 kernel: [  101.672098] rc rc0: lirc_dev: driver dvb_usb_rtl28xxu registered at minor = 0, raw IR receiver, no transmitter
Feb  6 16:38:38 CQ2WL13 kernel: [  101.672147] input: Trekstor DVB-T Stick Terres 2.0 as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3.2/rc/rc0/input27
Feb  6 16:38:38 CQ2WL13 kernel: [  101.672217] usb 1-1.3.2: dvb_usb_v2: schedule remote query interval to 200 msecs
Feb  6 16:38:38 CQ2WL13 kernel: [  101.681027] usb 1-1.3.2: dvb_usb_v2: 'Trekstor DVB-T Stick Terres 2.0' successfully initialized and connected
Feb  6 16:38:39 CQ2WL13 kernel: [  101.768277] usb 1-1.3.3: new high-speed USB device number 18 using xhci_hcd
Feb  6 16:38:39 CQ2WL13 kernel: [  101.881325] usb 1-1.3.3: New USB device found, idVendor=05e3, idProduct=0608, bcdDevice= 7.02
Feb  6 16:38:39 CQ2WL13 kernel: [  101.881327] usb 1-1.3.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb  6 16:38:39 CQ2WL13 kernel: [  101.881328] usb 1-1.3.3: Product: USB2.0 Hub
Feb  6 16:38:39 CQ2WL13 kernel: [  101.882218] hub 1-1.3.3:1.0: USB hub found
Feb  6 16:38:39 CQ2WL13 kernel: [  101.882474] hub 1-1.3.3:1.0: 4 ports detected
Feb  6 16:38:39 CQ2WL13 kernel: [  101.972238] usb 1-1.3.4: new high-speed USB device number 19 using xhci_hcd
Feb  6 16:38:39 CQ2WL13 kernel: [  102.147589] usb 1-1.3.4: New USB device found, idVendor=0bda, idProduct=402e, bcdDevice= 0.01
Feb  6 16:38:39 CQ2WL13 kernel: [  102.147590] usb 1-1.3.4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Feb  6 16:38:39 CQ2WL13 kernel: [  102.147591] usb 1-1.3.4: Product: USB Audio
Feb  6 16:38:39 CQ2WL13 kernel: [  102.147592] usb 1-1.3.4: Manufacturer: Generic
Feb  6 16:38:39 CQ2WL13 kernel: [  102.147593] usb 1-1.3.4: SerialNumber: 200901010001
Feb  6 16:38:39 CQ2WL13 kernel: [  102.216200] usb 1-1.3.3.2: new full-speed USB device number 20 using xhci_hcd
Feb  6 16:38:39 CQ2WL13 kernel: [  102.320810] usb 1-1.3.3.2: New USB device found, idVendor=0b0e, idProduct=0313, bcdDevice= 2.07
Feb  6 16:38:39 CQ2WL13 kernel: [  102.320811] usb 1-1.3.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb  6 16:38:39 CQ2WL13 kernel: [  102.320812] usb 1-1.3.3.2: Product: Jabra EVOLVE 30 II
Feb  6 16:38:39 CQ2WL13 kernel: [  102.320813] usb 1-1.3.3.2: Manufacturer: GN Audio A/S
Feb  6 16:38:39 CQ2WL13 kernel: [  102.320814] usb 1-1.3.3.2: SerialNumber: 000161F7661607
Feb  6 16:38:40 CQ2WL13 kernel: [  102.921644] usb 1-1.3.3.2: 1:1: cannot get freq at ep 0x83
Feb  6 16:38:40 CQ2WL13 kernel: [  102.924666] usb 1-1.3.3.2: 2:1: cannot get freq at ep 0x4
Feb  6 16:38:40 CQ2WL13 kernel: [  102.943559] input: GN Audio A/S Jabra EVOLVE 30 II as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3.2/1-1.3.3.2:1.3/0003:0B0E:0313.0006/input/input28
Feb  6 16:38:40 CQ2WL13 kernel: [  103.000357] usb 1-1.3.5: new high-speed USB device number 21 using xhci_hcd
Feb  6 16:38:40 CQ2WL13 kernel: [  103.004679] jabra 0003:0B0E:0313.0006: input,hiddev1,hidraw2: USB HID v1.00 Device [GN Audio A/S Jabra EVOLVE 30 II] on usb-0000:00:14.0-1.3.3.2/input3
Feb  6 16:38:40 CQ2WL13 kernel: [  103.109630] usb 1-1.3.5: New USB device found, idVendor=413c, idProduct=b06f, bcdDevice= 1.01
Feb  6 16:38:40 CQ2WL13 kernel: [  103.109631] usb 1-1.3.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb  6 16:38:40 CQ2WL13 kernel: [  103.109632] usb 1-1.3.5: Product: Dell dock
Feb  6 16:38:40 CQ2WL13 kernel: [  103.113857] hid-generic 0003:413C:B06F.0007: hiddev2,hidraw3: USB HID v1.11 Device [Dell dock] on usb-0000:00:14.0-1.3.5/input0
Feb  6 16:38:40 CQ2WL13 kernel: [  103.188040] usb 1-1.3.3.3: new high-speed USB device number 22 using xhci_hcd
Feb  6 16:38:40 CQ2WL13 kernel: [  103.312263] usb 1-1.3.3.3: New USB device found, idVendor=045e, idProduct=0779, bcdDevice= 1.06
Feb  6 16:38:40 CQ2WL13 kernel: [  103.312264] usb 1-1.3.3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  6 16:38:40 CQ2WL13 kernel: [  103.312265] usb 1-1.3.3.3: Product: Microsoft® LifeCam HD-3000
Feb  6 16:38:40 CQ2WL13 kernel: [  103.312266] usb 1-1.3.3.3: Manufacturer: Microsoft
Feb  6 16:38:40 CQ2WL13 kernel: [  103.648074] **usb usb3: root hub lost power or was reset**
Feb  6 16:38:40 CQ2WL13 kernel: [  103.648075] **usb usb4: root hub lost power or was reset**
Feb  6 16:38:41 CQ2WL13 kernel: [  103.754190] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam HD-3000 (045e:0779)
Feb  6 16:38:41 CQ2WL13 kernel: [  103.902606] input: Microsoft® LifeCam HD-3000: Mi as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3.3/1-1.3.3.3:1.0/input/input29
Feb  6 16:38:42 CQ2WL13 kernel: [  105.235552] usb 1-1.3.3.2: 2:1: cannot get freq at ep 0x4

#lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0781:5583 SanDisk Corp. Ultra Fit
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0a5c:5843 Broadcom Corp. 58200
Bus 001 Device 003: ID 1bcf:28c4 Sunplus Innovation Technology Inc. Integrated_Webcam_HD
Bus 001 Device 008: ID 8087:0aaa Intel Corp. 
Bus 001 Device 016: ID 413c:b06e Dell Computer Corp. 
Bus 001 Device 021: ID 413c:b06f Dell Computer Corp. 
Bus 001 Device 019: ID 0bda:402e Realtek Semiconductor Corp. 
Bus 001 Device 022: ID 045e:0779 Microsoft Corp. LifeCam HD-3000
Bus 001 Device 020: ID 0b0e:0313 GN Netcom 
Bus 001 Device 018: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 017: ID 1f4d:c803 G-Tek Electronics Group 
Bus 001 Device 015: ID 0bda:5413 Realtek Semiconductor Corp. 
Bus 001 Device 014: ID 0bda:5487 Realtek Semiconductor Corp. Dell dock
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

