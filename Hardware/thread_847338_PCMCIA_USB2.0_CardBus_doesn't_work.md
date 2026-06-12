---
title: "PCMCIA USB2.0 CardBus doesn't work"
date: 2008-07-02
forum: Hardware
---

### Post by Innuendo108 on 2008-07-02
I've bought VIA PCMCIA USB 2.0 CardBus Adapter and it doesn't work =(
I have Toshiba Satellite L35-A1054
Ubuntu 8.04; 2.6.24-19-generic
(I've installed pcmcia-cs)

[quote="dmesg | tail  *(with attached device)"]
[  446.773556] hub 4-0:1.0: connect-debounce failed, port 1 disabled
[  446.773762] hub 4-0:1.0: over-current change on port 2
[  448.796139] hub 4-0:1.0: over-current change on port 1
[  450.818425] printk: 1 messages suppressed.
[  450.818434] hub 4-0:1.0: connect-debounce failed, port 1 disabled
[  450.818637] hub 4-0:1.0: over-current change on port 2
[  452.845568] hub 4-0:1.0: over-current change on port 1
[  454.867119] printk: 1 messages suppressed.
[  454.867128] hub 4-0:1.0: connect-debounce failed, port 1 disabled
[  454.867333] hub 4-0:1.0: over-current change on port 2
[/quote]

[quote="dmesg | tail  *(without attached device)"]
[ 1757.429458] hub 5-0:1.0: connect-debounce failed, port 1 disabled
[ 1757.429462] hub 5-0:1.0: cannot disable port 1 (err = -19)
[ 1757.429465] hub 5-0:1.0: hub_port_status failed (err = -19)
[ 1757.430083] uhci_hcd 0000:0a:00.1: HCRESET not completed yet!
[ 1757.430104] uhci_hcd 0000:0a:00.1: USB bus 5 deregistered
[ 1757.430153] ACPI: PCI interrupt for device 0000:0a:00.1 disabled
[ 1757.430216] ehci_hcd 0000:0a:00.2: remove, state 0
[ 1757.430223] usb usb6: USB disconnect, address 1
[ 1757.430455] ehci_hcd 0000:0a:00.2: USB bus 6 deregistered
[ 1757.430504] ACPI: PCI interrupt for device 0000:0a:00.2 disabled
[/quote]

[quote="sudo lshw | grep pcmcia  *(cutted)"]
  *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
[/quote]

Also, in Device Manager appears items "USB UHCI Controller" and "USB EHCI Controller" when I attach new PCMCIA device.
Here is screenshot with summary of it from program "Device Manager"
[http://img108.imageshack.us/img108/3530/screenshotir5.png](http://img108.imageshack.us/img108/3530/screenshotir5.png)

---

