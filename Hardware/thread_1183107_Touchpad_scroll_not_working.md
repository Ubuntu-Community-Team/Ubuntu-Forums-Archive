---
title: "Touchpad scroll not working"
date: 2009-06-09
forum: Hardware
---

### Post by Bigfish051 on 2009-06-09
hello


i have a problem with touchpad horizontal and vertical scrolling. ubuntu is not recognizing any of edges (right or bottom) as scroll controls. i tried to fix it by checking and unchecking "enable vertical scrolling" in system > preferences > mouse > touchpad but no use

that issue did not exist while my laptop was running with ubuntu 8.10, but after 9.04 update my touchpad scroll failed

would you please help me fix this problem because it's really annoying.
i'm a total linux noob so please have understanding.

here's my configuration shortly:
> cpu:                                                           
                       Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz, 800 MHz
                       Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz, 2500 MHz
keyboard:
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      ETPS/2 Elantech Touchpad
graphics card:
                       nVidia GeForce 8600M GT
sound:
                       Intel 82801H (ICH8 Family) HD Audio Controller
storage:
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
network:
  wlan0                Atheros AR242x 802.11abg Wireless PCI Express Adapter
  eth0                 Broadcom NetLink BCM5787M Gigabit Ethernet PCI Express
network interface:
  pan0                 Ethernet network interface
  wlan0                WLAN network interface
  wmaster0             Network Interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sda             Hitachi HTS54252
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
cdrom:
  /dev/sr0             Optiarc DVD RW AD-7530B
usb controller:
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #1
                       Intel 82801H (ICH8 Family) USB UHCI Controller #3
                       Intel 82801H (ICH8 Family) USB UHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #1
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #5
                       Intel 82801H (ICH8 Family) USB UHCI Contoller #4
bios:
                       BIOS
bridge:
                       Intel 82801HEM (ICH8M) LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801H (ICH8 Family) PCI Express Port 6
                       Intel 82801H (ICH8 Family) PCI Express Port 5
                       Intel 82801H (ICH8 Family) PCI Express Port 4
                       Intel 82801H (ICH8 Family) PCI Express Port 3
                       Intel 82801H (ICH8 Family) PCI Express Port 2
                       Intel 82801H (ICH8 Family) PCI Express Port 1
                       Intel Mobile PM965/GM965/GL960 PCI Express Root Port
                       Intel Mobile PM965/GM965/GL960 Memory Controller Hub
hub:
                       Linux 2.6.28-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-11-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.28-11-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.28-11-generic ehci_hcd EHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
bluetooth:
                       Broadcom BCM92045NMD
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Ricoh R5C592 Memory Stick Bus Host Adapter
                       Ricoh R5C843 MMC Host Controller
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Intel 82801H (ICH8 Family) SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       TouchStrip Fingerprint Sensor
                       Chicony Electronics USB 2.0 Camera

p.s. sorry for bad english ):P

---

### Post by Bigfish051 on 2009-06-10
nothing?



there must be some kind of fix because it worked with ubuntu 8.10


edit:

fix:
(be careful because after first command your mouse won't work. second command makes it work and third makes module permanent):
```
sudo modprobe -r psmouse
modprobe psmouse proto=imps
echo "options psmouse proto=imps" | sudo tee -a /etc/modprobe.d/options.conf
```

---

