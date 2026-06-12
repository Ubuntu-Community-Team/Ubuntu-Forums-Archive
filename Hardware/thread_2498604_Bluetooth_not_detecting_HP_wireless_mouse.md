---
title: "Bluetooth not detecting HP wireless mouse"
date: 2024-06-21
forum: Hardware
---

### Post by ludwich on 2024-06-21
Hello everyone,

I'm trying to connect my wireless HP mouse on my laptop (Ubuntu 22.04.4) but it cannot even find it. 

I tried to scan manually via the terminal using ```
bluetoothctl
``` but it still does not appear. I can connect the mouse to other computers or connect a bluetooth headphone to this computer, so I think that the problem comes from their compatibility.

Also this PC was first under Windows 11, the mouse was connecting under Windows but not anymore since it has been switched to Ubuntu.


```
rfkill 
``` shows that nothing is blocked.

The model of the mouse is:  [SIZE=3][SIZE=2]HP 425 Programmable Bluetooth Mouse (7M1D5AA)


The output of ```
 hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 6C:F6:DA:5D:A6:41  ACL MTU: 1021:4  SCO MTU: 96:6
    UP RUNNING PSCAN 
    RX bytes:2331456 acl:152 sco:0 events:320316 errors:0
    TX bytes:309922502 acl:318655 sco:0 commands:770 errors:0
    Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: PERIPHERAL ACCEPT 
    Name: '-------'
    Class: 0x7c010c
    Service Classes: Rendering, Capturing, Object Transfer, Audio, Telephony
    Device Class: Computer, Laptop
    HCI Version:  (0xc)  Revision: 0x35fc
    LMP Version:  (0xc)  Subversion: 0x35fc
    Manufacturer: Intel Corp. (2)

```


Here is the output of [/SIZE][/SIZE]```
[SIZE=3][SIZE=2]dmesg | grep -i 'bluetooth'[/SIZE][/SIZE][SIZE=3][SIZE=2]
[    2.846671] Bluetooth: Core ver 2.22
[    2.846700] NET: Registered PF_BLUETOOTH protocol family
[    2.846701] Bluetooth: HCI device and connection manager initialized
[    2.846707] Bluetooth: HCI socket layer initialized
[    2.846709] Bluetooth: L2CAP socket layer initialized
[    2.846715] Bluetooth: SCO socket layer initialized
[    2.867994] Bluetooth: hci0: Device revision is 0
[    2.867999] Bluetooth: hci0: Secure boot is enabled
[    2.868000] Bluetooth: hci0: OTP lock is enabled
[    2.868001] Bluetooth: hci0: API lock is enabled
[    2.868002] Bluetooth: hci0: Debug lock is disabled
[    2.868003] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    2.868005] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[    2.869913] Bluetooth: hci0: Found device firmware: intel/ibt-0040-0041.sfi
[    2.869934] Bluetooth: hci0: Boot Address: 0x100800
[    2.869935] Bluetooth: hci0: Firmware Version: 252-24.23
[    3.773244] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.773250] Bluetooth: BNEP filters: protocol multicast
[    3.773255] Bluetooth: BNEP socket layer initialized
[    4.556129] Bluetooth: hci0: Waiting for firmware download to complete
[    4.556133] Bluetooth: hci0: Firmware loaded in 1646695 usecs
[    4.556246] Bluetooth: hci0: Waiting for device to boot
[    4.573981] Bluetooth: hci0: Device booted in 17413 usecs
[    4.574015] Bluetooth: hci0: Malformed MSFT vendor event: 0x02
[    4.575005] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-0040-0041.ddc
[    4.578207] Bluetooth: hci0: Applying Intel DDC parameters completed
[    4.582120] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[    4.660151] Bluetooth: MGMT ver 1.22
[   18.370503] Bluetooth: RFCOMM TTY layer initialized
[   18.370510] Bluetooth: RFCOMM socket layer initialized
[   18.370514] Bluetooth: RFCOMM ver 1.11
[   77.136545] Bluetooth: hci0: Ignoring error of Inquiry Cancel command
[  237.207057] Bluetooth: hci0: urb 0000000027409927 failed to resubmit (2)
[  237.207100] Bluetooth: hci0: urb 00000000c8ac5ae3 failed to resubmit (2)
[  243.659009] Bluetooth: hci0: Firmware timestamp 2023.24 buildtype 1 build 67068
[  243.661584] Bluetooth: hci0: Found device firmware: intel/ibt-0040-0041.sfi
[  243.661622] Bluetooth: hci0: Boot Address: 0x100800
[  243.661626] Bluetooth: hci0: Firmware Version: 252-24.23
[  243.661630] Bluetooth: hci0: Firmware already loaded
[  243.732120] Bluetooth: MGMT ver 1.22
[  254.108397] Bluetooth: hci0: Ignoring error of Inquiry Cancel command
[  643.008458] Bluetooth: hci0: Opcode 0x0401 failed: -16
[ 8084.957057] Bluetooth: hci0: Opcode 0x0401 failed: -16
[/SIZE][/SIZE]
```[SIZE=3][SIZE=2][SIZE=3][SIZE=2]

[/SIZE][/SIZE]

Thank you in advance for your help.
[/SIZE][/SIZE]

---

### Post by #&amp;thj^% on 2024-06-21
Will it show up with this?:
```
lsusb | grep "Wireless Mouse"
```
HP has some interesting firmware, but it also states>>"Compatible with Windows® 10 and higher, Chrome, and Mac®."

---

### Post by ludwich on 2024-06-24
It does not show up :/ 
Yes I've seen in the characteristics that Ubuntu is not mentioned but I was wondering if someone had a workaround. I don't really understand why a bluetooth device could only be accessible from a specific OS as the bluetooth card is the same anyway and although the drivers might change, I'm sure it's possible to reproduce the behavior of a specific OS. Maybe it's a lot of work and there isn't any easy solution, I'm a complete newbie in this field.

---

### Post by #&amp;thj^% on 2024-06-24
As i already pointed out, this device was written for just>>"Compatible with Windows® 10 and higher, Chrome, and Mac®." 

We/You need to find a developer that will reverse engineer the firmware for Linux. (Might be a task no one wants)

With respect there are numerous other Mice that work with linux OOTB

Wish I had better News for you.

---

### Post by him610 on 2024-06-24
Here is what the specs say...
> Compatible operating systems     Windows 11; Windows 10; macOS; ChromeOS
No Linux on there.

---

