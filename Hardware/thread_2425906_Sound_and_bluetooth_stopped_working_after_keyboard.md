---
title: "Sound and bluetooth stopped working after keyboard replacement (18.04)"
date: 2019-09-01
forum: Hardware
---

### Post by dbargteil on 2019-09-01
I replaced the keyboard in my ASUS Zenbook UX330 yesterday, on which I run Ubuntu 18.04. Prior to the replacement, everything was working (except for certain keys of the keyboard, hence the replacement).

For context, the motherboard is in two pieces, the smaller of which carries the WiFi card (Intel 8260NGW), the headphone jack, and a small chip with the Realtek logo ([see picture]("https://i.stack.imgur.com/3SOtN.jpg")). This small board is connected to the main board by a copper colored ribbon. The WiFi works, and I think the Bluetooth is handled by the same hardware device, so while my first suspicion was that  cable wasn't connected well, I'm unsure as to why one would be working and not the other. The bluetooth status bar icon shows bluetooth as on, but in the system settings under bluetooth it says "No bluetooth found". Also, this is probably obvious to people who are better versed in this, but ALSA seems to only be discovering whatever hardware handles HDMI out rather than the normal soundcard (I'm suspicious that I haven't seen "Realtek" in anything I've looked at). 

My hope in posting this here is as much as determining if this is an issue of device detection etc. versus if it's possible to tell that there is a hardware problem (e.g. loose connection). 

I don't know if this is important, but I did power up the system at one point and WiFi was not working and also the computer was spontaneously restarting -- I suspect this was due to contact between the metal keyboard backing and the motherboard. I've fixed this by transferring over the old backlight cover from the original keyboard to the new one and re-seating the copper ribbon and making sure it was connected. However, I imagine it's possible that during those boots that the OS lost track of devices on the small piece of motherboard that wasn't properly connected.

ALSA info: [http://alsa-project.org/db/?f=267ad710fca93b26e06a0517c50339a4b6795c76](http://alsa-project.org/db/?f=267ad710fca93b26e06a0517c50339a4b6795c76)

```
ps -e | grep blue

1067 ?        00:00:00 bluetoothd
2950 ?        00:00:02 indicator-bluet

```

```
lspci -nnk | grep -iA2 net02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
        Subsystem: Intel Corporation Wireless 8260 [8086:0110]
        Kernel driver in use: iwlwifi

```

```
rfkill list all0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f3:0903 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 04f2:b57a Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
hciconfig -a
hci0:   Type: Primary  Bus: USB
        BD Address: A0:AF:BD:8D:E8:BA  ACL MTU: 1021:4  SCO MTU: 96:6
        UP RUNNING PSCAN 
        RX bytes:79403 acl:0 sco:0 events:4197 errors:0
        TX bytes:610346 acl:0 sco:0 commands:2823 errors:0
        Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH SNIFF 
        Link mode: SLAVE ACCEPT 
        Name: 'dzbee-UX330UAK'
        Class: 0x10010c
        Service Classes: Object Transfer
        Device Class: Computer, Laptop
        HCI Version: 4.2 (0x8)  Revision: 0x100
        LMP Version: 4.2 (0x8)  Subversion: 0x100
        Manufacturer: Intel Corp. (2)

```

```
dmesg | egrep -i 'blue|firm'
[    0.028000] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.072636] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.038472] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[    1.038482] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[    1.760908] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    4.776531] iwlwifi 0000:02:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[    4.894171] Bluetooth: Core ver 2.22
[    4.894187] Bluetooth: HCI device and connection manager initialized
[    4.894190] Bluetooth: HCI socket layer initialized
[    4.894192] Bluetooth: L2CAP socket layer initialized
[    4.894196] Bluetooth: SCO socket layer initialized
[    4.921432] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[    4.928427] Bluetooth: hci0: Device revision is 5
[    4.928429] Bluetooth: hci0: Secure boot is enabled
[    4.928429] Bluetooth: hci0: OTP lock is enabled
[    4.928430] Bluetooth: hci0: API lock is enabled
[    4.928431] Bluetooth: hci0: Debug lock is disabled
[    4.928432] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    4.930903] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[    6.336789] Bluetooth: hci0: Waiting for firmware download to complete
[    6.337381] Bluetooth: hci0: Firmware loaded in 1386771 usecs
[    6.337418] Bluetooth: hci0: Waiting for device to boot
[    6.348389] Bluetooth: hci0: Device booted in 10722 usecs
[    6.430024] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
[    6.433395] Bluetooth: hci0: Applying Intel DDC parameters completed
[    6.794222] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.794224] Bluetooth: BNEP filters: protocol multicast
[    6.794227] Bluetooth: BNEP socket layer initialized
[  115.882159] Bluetooth: RFCOMM TTY layer initialized
[  115.882165] Bluetooth: RFCOMM socket layer initialized
[  115.882169] Bluetooth: RFCOMM ver 1.11

```

UPDATE: Some extra info -- when I try to use ```
bluetoothctl
``` to pair, trust, connect to a bluetooth speaker, it fails when connecting. It had connected to it in the past and just to test things out, I removed the speaker from the devices list and waited for the laptop to rediscover the device while scanning, and it was able to do so.

---

### Post by him610 on 2019-09-01
This is your bluetooth device. ```
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
```
Wired connection better, more reliable than bluetooth.
Some folks consider bluetooth not yet ready for prime time.

If you search on term, *[COLOR="#FF0000"]8087:0a2b[/COLOR]*, you will find several references to issues, resolutions, and bugs about the device.

---

