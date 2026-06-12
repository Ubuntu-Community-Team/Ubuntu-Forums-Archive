---
title: "USB-3.0 Ports on Toshiba LX835 not working under 16.04.3 release"
date: 2017-09-22
forum: Hardware
---

### Post by DAB4970 on 2017-09-22
The USB-3.0 ports on the left side of this Toshiba all-in-one, separate from the four usb-2 ports on the back panel.  I shall copy and paste here what LSHW shows for the 3.0 ports.

> *-usb:0             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:24 memory:c8600000-c860ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-93-generic xhci-hcd
                physical id: 0
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-93-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s

These ports give power to my WD 1-TB Passport drive, but doesn't auto-mount or show up in the list of devices in "disks" utility.  Could this be a driver issue?

---

### Post by Autodave on 2017-09-24
Have you tried connecting the drive to a USB2 port? What happens if you do?

---

### Post by DAB4970 on 2017-09-26
It mounts on a USB2 port, and shows up on the "disks" app as it should.  When I plugged it in to a USB2 port on other desktop, I remember Ubuntu telling me that the USB3 HD is plugged into an incorrect port.

---

### Post by Autodave on 2017-09-26
From what you posted, it appears that only one port is USB3. Have you tried both ports that you believe are USB3?

---

### Post by DAB4970 on 2017-09-27
There are 4 USB2 ports on the back panel and 2 USB3 ports on the left side.  I have tried both USB3 ports.

I recently replaced this motherboard which had Bios version 1.1, which I finally got updated to 6.2 a week or so ago.  I could open it up a verify again that all connections are attached to where they are supposed to be.

---

### Post by Autodave on 2017-09-27
I looked that PC up on line and it does state that it has two USB3 ports, but what you printed out before is only showing one USB3.

---

### Post by frogotronic on 2017-09-27
No.  It is very likley that your USB 3.0 ports are fully working.  Your WD drive is likely using firmware/hardware that is not USB 3.0 compliant.  To check this, try inserting a SANDISK or KINGSTON USB 3.0 thumbdrive into your USB 3.0 port.  If it is recognised, it is your HDD.

---

### Post by DAB4970 on 2017-09-27
Thanks frogotronic.  I put a thumb drive into both of them and they mounted correctly.  I'll have to figure out a way to update it's firmware, since Windows is not an option for me.

---

