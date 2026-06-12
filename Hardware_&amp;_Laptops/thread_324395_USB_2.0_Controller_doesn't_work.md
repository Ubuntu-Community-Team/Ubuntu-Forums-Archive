---
title: "USB 2.0 Controller doesn't work"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by uboltun on 2006-12-23
I cant get to work a PCI USB 2.0 controller in my computer for some reason. 
I connected my Ipod to one of the ports and this is what I get when running 

sudo rmmod ehci_hcd
sudo modprob ehci_hcd
dmesg

ehci_hcd 0000:02:0d.3: remove, state 1
usb usb4: USB disconnect, address 1
ehci_hcd 0000:02:0d.3: USB bus 4 deregistered
hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
PCI: Found IRQ 3 for device 0000:02:0d.3
ehci_hcd 0000:02:0d.3: EHCI Host Controller
ehci_hcd 0000:02:0d.3: debug port 1
PCI: cache line size of 128 is not supported by device 0000:02:0d.3
ehci_hcd 0000:02:0d.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:02:0d.3: irq 3, io mem 0xfeaff800
ehci_hcd 0000:02:0d.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
hub 4-0:1.0: over-current change on port 1
hub 4-0:1.0: over-current change on port 2
hub 4-0:1.0: over-current change on port 3
hub 4-0:1.0: over-current change on port 4
hub 4-0:1.0: over-current change on port 5
hub 4-0:1.0: over-current change on port 6

When listing USB devices Ipod is not there.
:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0bb2:0304 Ambit Microsystems Corp.
Bus 002 Device 002: ID 069a:4501 Askey Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner] (rev a4)
0000:02:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:0c.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
0000:02:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)


Ipod is working on USB 1.1 ports , so it is not a problem. I also turned off acpi=off as suggested in some posts. 

Any ideas ?

---

