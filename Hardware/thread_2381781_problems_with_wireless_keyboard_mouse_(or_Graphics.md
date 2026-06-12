---
title: "problems with wireless keyboard mouse (or Graphics or compiz?)"
date: 2018-01-05
forum: Hardware
---

### Post by tekborayaccount on 2018-01-05
Hi,

I have a workstation with 2 Xeon CPUs with many cores, 1 NVIDIA GTX1050, 1 NVIDIA TESLA K40 (Computing only).

I have recently upgraded ubuntu from 14 to 16.04 LTS. It went into unsuccessfull login-loop. Reinstalled unity, compiz couple of times, uninstalled nvidia drivers and reinstall solved the login. Now I am having issues with wireless mouse and keyboard lag-freeze occasionally. Cable mouse works smoothly. I am suspecting that it can be still be an issue with the drivers or desktop integration with cards. Please let me know what I should post here to help resolving the problem. 
Below are my queries and whatever they return.
```

1.
$nvidia-detector
none



$ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro free

== /sys/devices/pci0000:80/0000:80:01.0/0000:81:00.0 ==
model    : GK110BGL [Tesla K40c]
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001024sv000010DEsd00000983bc03sc02i00
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - third-party free

== /sys/devices/pci0000:00/0000:00:02.0/0000:03:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001B81sv00001043sd000085A0bc03sc00i00
driver   : nvidia-381 - third-party free
driver   : nvidia-387 - third-party free recommended
driver   : nvidia-384 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin


$ lsdev
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:11.4             46    0000-0000   0000-0000   0000-0000   0000-0000   0000-0000
0000:00:1f.2             52    0000-0000   0000-0000   0000-0000   0000-0000   0000-0000
0000:00:1f.3                   0000-0000
0000:03:00.0                     0000-0000
0000:06:00.0                     0000-0000
0000:07:00.0                     0000-0000
0000:08:00.0             58      0000-0000     0000-0000     0000-0000     0000-0000     0000-0000
acpi                      9 
ACPI                           0000-0000   0000-0000   0000-0000   0000-0000   0000-0000   0000-0000
aerdrv, PCIe PME      25 26 28 30 36 
ahci                               0000-0000       0000-0000       0000-0000       0000-0000       0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000     0000-0000
APEI                           0000-0000
cascade             4       
dma                            0000-0000
dma1                           0000-0000
dma2                           0000-0000
dmar0                    72 
dmar1                    73 
ehci_hcd:usb2            18 
eth0                     47 
eth0-TxRx-0              48 
eth0-TxRx-1              49 
eth0-TxRx-2              50 
eth0-TxRx-3              51 
eth1                     53 
eth1-TxRx-0              54 
eth1-TxRx-1              55 
eth1-TxRx-2              56 
eth1-TxRx-3              57 
fpu                            0000-0000
i8042                  1 12 
iTCO_wdt.0.auto                0000-0000   0000-0000
keyboard                       0000-0000   0000-0000
nvidia                59 62 
PCI                          0000-0000 0000-0000 0000-0000   0000-0000   0000-0000   0000-0000   0000-0000 0000-0000
PCIe PME              31 32 33 34 
pic1                           0000-0000
pic2                           0000-0000
pnp                            0000-0000   0000-0000     0000-0000   0000-0000   0000-0000   0000-0000
PNP0800:00                     0000-0000
PNP0C04:00                       0000-0000
rtc0                      8    0000-0000
serial                         0000-0000   0000-0000
snd_hda_intel         60 61 
timer                     0 
timer0                         0000-0000
timer1                         0000-0000
vesafb                         0000-0000
xhci-hcd:usb3            19 
xhci_hcd              38 39 40 41 42 43 44 45 





$ sudo lsusb
Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 004: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo lshw | grep USB
                description: USB controller
                product: ASM1042A USB 3.0 Host Controller
             description: USB controller
             product: C610/X99 series chipset USB xHCI Host Controller
                   description: USB hub
                   description: USB hub
             description: USB controller
             product: C610/X99 series chipset USB Enhanced Host Controller #2
                   description: USB hub
             description: USB controller
             product: C610/X99 series chipset USB Enhanced Host Controller #1
                   description: USB hub


$ sudo lshw  | grep -i NVIDIA
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                configuration: driver=nvidia latency=0
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
             vendor: NVIDIA Corporation
             configuration: driver=nvidia latency=0


$ compiz --version
Compiz 0.9.12.2




```

---

### Post by sccman on 2018-01-05
I have a few questions about the devices:

1) What are the devices' make and model numbers?
2) How are the wireless devices connected (USB, Bluetooth, etc)?
3) Can the Ubuntu detect the wireless devices at all?

---

### Post by tekborayaccount on 2018-01-08
3) Ubuntu can detect the wireless devices. However, it causes occasional freezes and lags. The wired mouse runs smoothly even when the other freezes.
2) I think they are wireless connected, not bluetooth.
1) Microsoft 5050 Desktop Comfort Keyboard and mouse. Asus Nvidia GTX 1050 and Nvidia K40 Tesla. 

I will post NVIDIA BUG REPORT and Xorg file below if you can make any meaning out of it


[https://paste.ubuntu.com/26345855/](https://paste.ubuntu.com/26345855/)

---

### Post by sccman on 2018-01-09
Also you mentioned that you experienced issues with the mouse and keyboard. How would you describe these issues?

---

