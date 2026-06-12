---
title: "Strange behavior with pcmcia card (USB 2.0 hub)"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by chaffeur on 2007-11-09
Hi!
I've been googling around for a while and reading on these forums but i haven't found a solution for my problems. So here goes;
I'm using an old Dell Latitude C610, which has no USB 2.0 ports, only one 1.1 port. So I've bought a pcmcia card (which seems to be using the yenta_cardbus driver) that has two USB 2.0 ports. This is what I get when I plug it in:

dmesg | tail
> [  362.296000] ehci_hcd 0000:07:00.2: EHCI Host Controller
[  362.296000] ehci_hcd 0000:07:00.2: new USB bus registered, assigned bus number 4
[  362.296000] ehci_hcd 0000:07:00.2: irq 11, io mem 0x3c000200
[  362.296000] ehci_hcd 0000:07:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  362.296000] usb usb4: configuration #1 chosen from 1 choice
[  362.296000] hub 4-0:1.0: USB hub found
[  362.296000] hub 4-0:1.0: 4 ports detected
[  362.704000] hub 4-0:1.0: over-current change on port 3
[  362.808000] hub 4-0:1.0: over-current change on port 4


First of all, it finds four ports! How come? Well, it seems to be USB 2.0, because it says ehci_hcd.
But when i look in lshw..:

sudo lshw:
> 
................ *-pcmcia:0
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
........
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
.............
     *-usb:0
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 0
          bus info: pci@0000:07:00.0
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: pm uhci bus_master cap_list
          configuration: driver=uhci_hcd latency=22 module=uhci_hcd
     *-usb:1
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 0.1
          bus info: pci@0000:07:00.1
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: pm uhci bus_master cap_list
          configuration: driver=uhci_hcd latency=22 module=uhci_hcd
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: VIA Technologies, Inc.
          physical id: 0.2
          bus info: pci@0000:07:00.2
          version: 63
          width: 32 bits
          clock: 33MHz
          capabilities: pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=22 module=ehci_hcd


I have cut away what i belive is uninteresting. In this listing it finds one ehci_hcd port! but if i plug in for example a webcam it just use uhci_hcd:

dmesg | tail:
> [ 1063.116000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 1063.308000] usb 2-2: configuration #1 chosen from 1 choice
[ 1063.312000] /home/***/gspcav1-20070508/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[ 1063.312000] /home/***/gspcav1-20070508/gspca_core.c: [spca5xx_probe:4098] Camera type JPEG 
[ 1063.312000] /home/***/gspcav1-20070508/Vimicro/zc3xx.h: [zc3xx_config:515] Sensor ID:22
[ 1063.976000] /home/***/gspcav1-20070508/Vimicro/zc3xx.h: [zc3xx_config:522] Find Sensor Tas5130 (VF0250)
[ 1063.980000] /home/***/gspcav1-20070508/gspca_core.c: [spca5xx_getcapability:1215] maxw 640 maxh 480 minw 176 minh 144


See? It just uses the uhci_hcd. Same this whatever i plug in (external hdd, usb flash, mp3 etc...).
I've tried modprobe -r uhci-hcd but that just makes all devices undetectable...
Anyone have any clue?
Thanks a lot for your time!
/David

---

### Post by chaffeur on 2007-11-12
Ok, a quick update:
I've noticed that if i connect another usbhub (usb2.0 -> 4 usb2.0 ports) to my usb pcmcia card i actually notices those ports as ehci-hcd:

dmesg | tail:
> [76042.416000] usb 4-1: USB disconnect, address 5
[76046.044000] usb 4-1: new high speed USB device using ehci_hcd and address 7
[76046.176000] usb 4-1: configuration #1 chosen from 1 choice
[76046.176000] hub 4-1:1.0: USB hub found
[76046.176000] hub 4-1:1.0: 4 ports detected


...then if i insert my cam, for example into one of *those* ports it notices those too as ehci:

dmesg | tail:
> [76126.116000] usb 4-1.4: new full speed USB device using ehci_hcd and address 8
[76126.208000] usb 4-1.4: configuration #1 chosen from 1 choice
[76126.208000] /home/***/gspcav1-20070508/gspca_core.c: USB GSPCA camera found.(ZC3XX)

but then if i try to use the cam the ports bandwidth get overflowed. So i can't use it.
Is there any way to "turn off" the ports i'm not using?
Thanks for your attention!
David

---

