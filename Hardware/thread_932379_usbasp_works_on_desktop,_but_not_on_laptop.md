---
title: "usbasp works on desktop, but not on laptop"
date: 2008-09-28
forum: Hardware
---

### Post by jay019 on 2008-09-28
OK, so I bought a USBasp programmer on ebay in the hope of moving development from my 533MHz desktop machine to my significantly faster laptop. The programmer is detected correctly when plugged into the desktop (running ubuntu 8.04) yet plugging it into the laptop (again ubuntu 8.04) it is not recognized at all.

Desktop: lsusb 
```
 
Bus 001 Device 002: ID 16c0:05dc (USBasp found) 
Bus 001 Device 001: ID 0000:0000 

``` 

tail -f /var/log/syslog 
```
 
Sep 28 23:54:01 avr-programmer kernel: [ 707.023391] usb 1-2: new low speed USB device using uhci_hcd and address 3 
Sep 28 23:54:01 avr-programmer kernel: [ 707.194742] usb 1-2: configuration #1 chosen from 1 choice 
Sep 28 23:54:01 avr-programmer NetworkManager: <debug> [1222611841.538319] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_16c0_5dc_noserial'). 
Sep 28 23:54:01 avr-programmer NetworkManager: <debug> [1222611841.928715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_16c0_5dc_noserial_if0').

```

----------------------------

Laptop: 

lsusb 
```
 
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) 
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 

``` 

tail -f /var/log/syslog 
```
 
Sep 28 23:48:32 kernel: [ 1025.884058] usb 2-2: new low speed USB device using uhci_hcd and address 60 
Sep 28 23:48:33 kernel: [ 1026.415199] usb 2-2: device not accepting address 60, error -71 
Sep 28 23:48:33 kernel: [ 1026.528098] usb 2-2: new low speed USB device using uhci_hcd and address 61 
Sep 28 23:48:34 kernel: [ 1027.106561] usb 2-2: device not accepting address 61, error -71 
Sep 28 23:48:34 kernel: [ 1027.218466] usb 2-2: new low speed USB device using uhci_hcd and address 62 
Sep 28 23:48:34 kernel: [ 1027.260464] usb 2-2: device descriptor read/8, error -71 
Sep 28 23:48:34 kernel: [ 1027.389344] usb 2-2: device descriptor read/8, error -71 
Sep 28 23:48:34 kernel: [ 1027.602082] usb 2-2: new low speed USB device using uhci_hcd and address 63 
Sep 28 23:48:34 kernel: [ 1027.632119] usb 2-2: device descriptor read/8, error -71 
Sep 28 23:48:34 kernel: [ 1027.762003] usb 2-2: device descriptor read/8, error -71 
Sep 28 23:48:35 kernel: [ 1028.105610] usb 2-2: new low speed USB device using uhci_hcd and address 64 
Sep 28 23:48:35 kernel: [ 1028.248528] usb 2-2: device descriptor read/all, error -71 
Sep 28 23:48:35 kernel: [ 1028.362370] usb 2-2: new low speed USB device using uhci_hcd and address 65 
Sep 28 23:48:35 kernel: [ 1028.889839] usb 2-2: device not accepting address 65, error -71 
Sep 28 23:48:35 kernel: [ 1029.001745] usb 2-2: new low speed USB device using uhci_hcd and address 66 
Sep 28 23:48:36 kernel: [ 1029.413335] usb 2-2: device not accepting address 66, error -71 
Sep 28 23:48:36 kernel: [ 1029.524216] usb 2-2: new low speed USB device using uhci_hcd and address 67 
Sep 28 23:48:36 kernel: [ 1029.554291] usb 2-2: device descriptor read/8, error -71 
Sep 28 23:48:36 kernel: [ 1029.684170] usb 2-2: device descriptor read/8, error -71 

``` 

The light on the board lights up with both the desktop and the laptop so power gets to the board no probs and the usb port on the laptop works fine, just has problems as shown in syslog which I have no idea how to work out.

If anyone can shed some light on this I would be very grateful.

EDIT: If it helps, I have tried modprobbing ehci_hcd & uhci_hcd 

Cheers.

---

### Post by sickasabat on 2009-11-21
Bump: I am having the same troubles on my laptop.

---

### Post by toface on 2010-02-28
I can say with almost 100% certainty that this is a bug in the code for the SiS chipset USB controller and only exists in 9.10 and above. By 'Programming' I mean using the USBAsp to flash the target processor. I have such a computer, and I've done the following steps:

1. Install 9.04
2. Programming works.
3. Upgrade to 9.10. Once I reboot, programming does not work and I get similar errors to the first poster.
4. Upgrade to 10.04 (alpha-stage), programming does not work.
5. Add USB-card (VIA-chipset)
6. Move the programmer to the new card, programming works
7. Move the programmer back to the motherboard connector, programming does not work.

Ie, downgrade to 9.04, add an usb-card or get a new computer and you should have no problems programming.

I will edit this post with a bug number once I've created the bug.

-- edit:
I will try to see if this is a flaw in the ubuntu patches or the upstream kernel before posting a bug report

Since the first post is from 08.04, it seems to either common for several chipsets or completely unrelated issues.

--edit:
Changing kernel does not help, even went back to the old 2.6.28-19 that I used with 9.04. I will NOT bugreport this, as I should have known that SiS chips would spell trouble (SiS USB-chips have a bad history of not even working with Windows)

---

