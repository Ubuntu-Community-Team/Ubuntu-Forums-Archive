---
title: "ipw2200 must be unloaded and loaded before it works"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by BungaMan on 2007-04-25
My wireless works fine, the only thing is that I first have to jump into a console to remove module ipw2200 and modprobe it again before it works.

/var/log/messages shows me (the long time is because of a file system check)

Apr 25 18:02:12 lapper kernel: [  113.264000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
// a bit more info from dmesg here
[  123.268000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[  123.268000] ipw2200: Unable to load firmware: -2
[  123.268000] ipw2200: failed to register network device
//
Apr 25 18:02:12 lapper kernel: [  123.268000] ACPI: PCI interrupt for device 0000:02:0d.0 disabled
Apr 25 18:02:12 lapper kernel: [  123.268000] ipw2200: probe of 0000:02:0d.0 failed with error -5
...
Apr 25 18:06:24 lapper kernel: [  499.260000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
Apr 25 18:06:24 lapper kernel: [  499.260000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Apr 25 18:06:24 lapper kernel: [  499.264000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Apr 25 18:06:24 lapper kernel: [  499.264000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Apr 25 18:06:24 lapper kernel: [  499.484000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Apr 25 18:06:42 lapper dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 25 18:06:44 lapper kernel: [  518.704000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 25 18:07:19 lapper kernel: [  554.284000] ipw2200: Firmware error detected.  Restarting.
...
Apr 25 18:07:30 lapper kernel: [  565.068000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Anyone who has an idea of what is going on here or even how to fix it?  Is it a bug that I should file?

---

### Post by BungaMan on 2007-04-26
*push up*

---

### Post by BungaMan on 2007-05-02
c'mon, don't be scared to reply.

---

### Post by extremecarver on 2007-05-16
I've got the same problems as you, however only with vanilla kernel.

Here are two of my dmesg outputs - first 2.6.22rc1 with CK patches, second ubuntu 2.6.20-15

> 17
[    6.188094] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[    6.188129] PM: Adding info for No Bus:0000:02:03.0
[   66.080702] PM: Removing info for No Bus:0000:02:03.0
[   66.080734] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   66.080783] ipw2200: Unable to load firmware: -2
[   66.080823] ipw2200: failed to register network device
[   66.080884] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[   66.080889] ipw2200: probe of 0000:02:03.0 failed with error -5
[   66.080900] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   66.080903] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   66.081097] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 

[   15.332000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   15.332000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.332000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   15.332000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   15.520000] Bluetooth: HCI USB driver ver 2.9
[   15.520000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[   15.628000] usbcore: registered new interface driver hci_usb
[   15.632000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ

Could you please post back with the commands you use to unload and load it?

---

### Post by extremecarver on 2007-05-18
For me it started working again after compiling the IPW2200 part of the kernel as module instead of directly inserted. Maybe you've got the same problem.

---

### Post by BungaMan on 2007-05-22
all I have to do is 
rmmod ipw2200
and
modprobe ipw2200
and wireless is working.  so yes, it is a module.  the kernel is out-of-the-box feisty vanilla so nothing special there.
I am a bit worried about te firmware errors...

---

### Post by BungaMan on 2007-05-23
WOW fixed !! I have a usb drive as well.  By all the bad luck in the world, its power connector and my laptop's fit on eachother (!!!) but the adapter for the usb drive gives a lower output.  When plugged into my portable, it can still run but slow as hell and as soon as more power is requested it does a hard shutdown.  It also caused some errors like above with the wireless

---

