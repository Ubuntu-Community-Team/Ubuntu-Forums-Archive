---
title: "Error ACPI on boot related with USB"
date: 2020-05-07
forum: Hardware
---

### Post by erogarcia on 2020-05-07
Hi!

I have a fresh installation of Ubuntu 20.04 and apparently the system works ok. But when I boot I can read some errors:

[INDENT]ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT1._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT2._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[...]
ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT13._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT14._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[/INDENT]

One error from POT1 to POT14 

My hardware: 

Asus ROG STRIX B450-F GAMING
AMD Ryzen 7 2700X 3.7 Ghz
2x Kingston HyperX Fury Black 16GB DDR4 3200Mhz PC-25600 CL16
NVIDIA GeForce 630 rev. 2

My dmseg says:
[...]

[    0.421320] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    0.421321] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.421322] usb usb1: Product: xHCI Host Controller
[    0.421323] usb usb1: Manufacturer: Linux 5.4.0-28-generic xhci-hcd
[    0.421323] usb usb1: SerialNumber: 0000:02:00.0
[    0.421382] hub 1-0:1.0: USB hub found
[    0.421394] hub 1-0:1.0: 10 ports detected
[    0.421476] No Local Variables are initialized for Method [_PLD]
[    0.421477] No Arguments are initialized for method [_PLD]
[    0.421478] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT5._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.421488] fbcon: Taking over console
[    0.421529] Console: switching to colour frame buffer device 240x67
[    0.422445] No Local Variables are initialized for Method [_PLD]
[    0.422446] No Arguments are initialized for method [_PLD]
[    0.422448] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT6._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422506] No Local Variables are initialized for Method [_PLD]
[    0.422507] No Arguments are initialized for method [_PLD]
[    0.422508] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT7._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422564] No Local Variables are initialized for Method [_PLD]
[    0.422565] No Arguments are initialized for method [_PLD]
[    0.422566] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT8._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422621] No Local Variables are initialized for Method [_PLD]
[    0.422622] No Arguments are initialized for method [_PLD]
[    0.422623] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT9._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422676] No Local Variables are initialized for Method [_PLD]
[    0.422677] No Arguments are initialized for method [_PLD]
[    0.422678] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO10._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422732] No Local Variables are initialized for Method [_PLD]
[    0.422733] No Arguments are initialized for method [_PLD]
[    0.422734] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO11._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422787] No Local Variables are initialized for Method [_PLD]
[    0.422788] No Arguments are initialized for method [_PLD]
[    0.422789] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO12._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422843] No Local Variables are initialized for Method [_PLD]
[    0.422844] No Arguments are initialized for method [_PLD]
[    0.422845] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO13._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.422899] No Local Variables are initialized for Method [_PLD]
[    0.422900] No Arguments are initialized for method [_PLD]
[    0.422901] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO14._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.423038] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    0.423040] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
[    0.423043] xhci_hcd 0000:02:00.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.423097] usb usb2: We don't know the algorithms for LPM for this host, disabling LPM.
[    0.423113] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.04
[    0.423114] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.423115] usb usb2: Product: xHCI Host Controller
[    0.423116] usb usb2: Manufacturer: Linux 5.4.0-28-generic xhci-hcd
[    0.423116] usb usb2: SerialNumber: 0000:02:00.0
[    0.423176] hub 2-0:1.0: USB hub found
[    0.423182] hub 2-0:1.0: 4 ports detected
[    0.423237] No Local Variables are initialized for Method [_PLD]
[    0.423238] No Arguments are initialized for method [_PLD]
[    0.423239] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT1._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.423300] No Local Variables are initialized for Method [_PLD]
[    0.423301] No Arguments are initialized for method [_PLD]
[    0.423302] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT2._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.423360] No Local Variables are initialized for Method [_PLD]
[    0.423361] No Arguments are initialized for method [_PLD]
[    0.423362] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT3._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.423420] No Local Variables are initialized for Method [_PLD]
[    0.423421] No Arguments are initialized for method [_PLD]
[    0.423422] ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT4._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20190816/psparse-529)
[    0.423555] xhci_hcd 0000:0b:00.3: xHCI Host Controller
[    0.423558] xhci_hcd 0000:0b:00.3: new USB bus registered, assigned bus number 3
[    0.423651] xhci_hcd 0000:0b:00.3: hcc params 0x0270f665 hci version 0x100 quirks 0x0000000000000410
[    0.423906] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    0.423907] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.423908] usb usb3: Product: xHCI Host Controller
[    0.423908] usb usb3: Manufacturer: Linux 5.4.0-28-generic xhci-hcd
[    0.423909] usb usb3: SerialNumber: 0000:0b:00.3
[    0.423966] hub 3-0:1.0: USB hub found
[    0.423971] hub 3-0:1.0: 4 ports detected
[    0.424105] xhci_hcd 0000:0b:00.3: xHCI Host Controller
[    0.424106] xhci_hcd 0000:0b:00.3: new USB bus registered, assigned bus number 4
[    0.424108] xhci_hcd 0000:0b:00.3: Host supports USB 3.0 SuperSpeed
[    0.424117] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
[    0.424129] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.04
[    0.424129] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.424130] usb usb4: Product: xHCI Host Controller
[    0.424131] usb usb4: Manufacturer: Linux 5.4.0-28-generic xhci-hcd
[    0.424131] usb usb4: SerialNumber: 0000:0b:00.3
[    0.424181] hub 4-0:1.0: USB hub found
[    0.424186] hub 4-0:1.0: 4 ports detected


[...]


Any idea?

Thanks in advance

---

### Post by P-I H on 2020-05-07
I have the same motherboard and the same ACPI error. 
```
ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.POT1._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20200110/psparse-529)
.....
ACPI Error: Aborting method \_SB.PCI0.GPP2.PTXH.RHUB.PO14._PLD due to previous error (AE_AML_UNINITIALIZED_ELEMENT) (20200110/psparse-529)
```
However I have not found any functionality impact.

I have W10, Fedora32 and Ubuntu 20.04 installed on this computer. On both Fedora and Ubuntu Logs give this info. I haven't seen any info on W10.

When I google with "AE_AML_UNINITIALIZED_ELEMENT) (20200110/psparse-529" I get some info
[https://bbs.archlinux.org/viewtopic.php?id=243991](https://bbs.archlinux.org/viewtopic.php?id=243991)
[https://bugzilla.redhat.com/show_bug.cgi?id=1610727](https://bugzilla.redhat.com/show_bug.cgi?id=1610727)
[https://bbs.archlinux.org/viewtopic.php?id=223804](https://bbs.archlinux.org/viewtopic.php?id=223804)

Probably this isn't important and can be ignored.
Full config
```
p-i@pi-Asus-B450-F:~$ inxi -Fz
System:    Kernel: 5.6.7-050607-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1373 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1373 2: 1373 3: 1375 4: 1372 5: 1375 6: 1371 7: 1374 
           8: 1372 9: 1373 10: 1375 11: 1379 12: 1374 13: 1373 14: 1375 15: 1373 16: 1372 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu 
           v: kernel 
           Display: wayland server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.36.0 5.6.7-050607-generic LLVM 9.0.1) 
           v: 4.6 Mesa 20.2.0-devel (git-d510974 2020-05-06 focal-oibaf-ppa) 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.6.7-050607-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 680.02 GiB used: 88.91 GiB (13.1%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 227.74 GiB used: 61.94 GiB (27.2%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 42.0 C mobo: 36.0 C gpu: amdgpu temp: 48 C 
           Fan Speeds (RPM): cpu: 551 case-1: 890 case-2: 824 case-3: 490 gpu: amdgpu fan: 0 
Info:      Processes: 363 Uptime: 9m Memory: 15.56 GiB used: 1.44 GiB (9.3%) Shell: bash inxi: 3.0.38 
p-i@pi-Asus-B450-F:~$

```

---

### Post by erogarcia on 2020-05-08
Hi P-I H,

I agree, probably can be ignored. Actually I have had no problems on ubuntu.

I want to check how ubuntu works with USB drives (in my old PC I had some USB problems with hardrives and pendrives), but it seems all OK.

---

