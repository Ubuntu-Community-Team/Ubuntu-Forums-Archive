---
title: "No Bluetooth - intel ac9260"
date: 2019-01-27
forum: Hardware
---

### Post by CordlezToaster on 2019-01-27
Hi All

Currently have an intel AC 9260 installed in my laptop. When Ubuntu 18.10 kernel 4.20.4 boots I don't have an active bluetooth controller and no bluetooth. 
Interestingly if i put my laptop to sleep and then wake it up, bluetooth works perfectly. I'd like to get it to a point where bluetooth works straight away after the laptops turned on.



```
    uname -a
    Linux tp-ThinkPad-E485 4.20.4-042004-generic #201901222207 SMP Tue Jan 22 22:09:25 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```  
```
  
    $ rfkill list
        0: phy0: Wireless LAN
        	Soft blocked: no
        	Hard blocked: no
        1: hci0: Bluetooth
        	Soft blocked: no
        	Hard blocked: no
    
```  
Output after laptop has woken from sleep/suspend (bluetooth then works)
```
  
    $ dmesg | egrep -i 'blue|firm'
    [    0.356392] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
    [    0.398494] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
    [    2.881280] Bluetooth: Core ver 2.22
    [    2.881309] Bluetooth: HCI device and connection manager initialized
    [    2.881330] Bluetooth: HCI socket layer initialized
    [    2.881333] Bluetooth: L2CAP socket layer initialized
    [    2.881340] Bluetooth: SCO socket layer initialized
    [    2.911239] iwlwifi 0000:04:00.0: loaded firmware version 41.fc1a7aea.0 op_mode iwlmvm
    [    3.132551] [drm] Found VCN firmware Version: 1.73 Family ID: 18
    [    3.132575] [drm] PSP loading VCN firmware
    [    3.311586] psmouse serio2: trackpoint: Elan TrackPoint firmware: 0x11, buttons: 3/3
    [    5.448940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [    5.448943] Bluetooth: BNEP filters: protocol multicast
    [    5.448949] Bluetooth: BNEP socket layer initialized
    [  264.225261] Bluetooth: hci0: Bootloader revision 0.1 build 42 week 52 2015
    [  264.228259] Bluetooth: hci0: Device revision is 2
    [  264.228262] Bluetooth: hci0: Secure boot is enabled
    [  264.228264] Bluetooth: hci0: OTP lock is enabled
    [  264.228265] Bluetooth: hci0: API lock is enabled
    [  264.228267] Bluetooth: hci0: Debug lock is disabled
    [  264.228269] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
    [  264.232137] Bluetooth: hci0: Found device firmware: intel/ibt-18-16-1.sfi
    [  265.541066] Bluetooth: hci0: Waiting for firmware download to complete
    [  265.541967] Bluetooth: hci0: Firmware loaded in 1289556 usecs
    [  265.542126] Bluetooth: hci0: Waiting for device to boot
    [  265.557996] Bluetooth: hci0: Device booted in 15574 usecs
    [  265.560048] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-18-16-1.ddc
    [  265.571987] Bluetooth: hci0: Applying Intel DDC parameters completed
    [  265.753188] Bluetooth: RFCOMM TTY layer initialized
    [  265.753194] Bluetooth: RFCOMM socket layer initialized
    [  265.753199] Bluetooth: RFCOMM ver 1.11
    [  266.018950] Bluetooth: hci0: last event is not cmd complete (0x0f)
    [  282.146608] Bluetooth: hci0: last event is not cmd complete (0x0f)
    [  285.107849] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
    [  285.107856] Bluetooth: HIDP socket layer initialized
    [  285.115102] input: MagicMouse as /devices/pci0000:00/0000:00:08.1/0000:05:00.4/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:256/0005:05AC:030D.0001/input/input16
    [  285.115312] magicmouse 0005:05AC:030D.0001: input,hidraw0: BLUETOOTH HID v3.06 Mouse [MagicMouse] on fc:77:74:eb:f6:2b


```  
After a freshboot here is the dmesg output (bluetooth doesn't work)
```
  
    $ dmesg | egrep -i 'blue|firm'
    [    0.360983] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
    [    0.399197] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
    [    2.848124] Bluetooth: Core ver 2.22
    [    2.848200] Bluetooth: HCI device and connection manager initialized
    [    2.848209] Bluetooth: HCI socket layer initialized
    [    2.848214] Bluetooth: L2CAP socket layer initialized
    [    2.848221] Bluetooth: SCO socket layer initialized
    [    2.872284] Bluetooth: hci0: Firmware revision 0.1 build 130 week 44 2018
    [    2.880174] iwlwifi 0000:04:00.0: loaded firmware version 41.fc1a7aea.0 op_mode iwlmvm
    [    3.131527] [drm] Found VCN firmware Version: 1.73 Family ID: 18
    [    3.131539] [drm] PSP loading VCN firmware
    [    3.331119] psmouse serio2: trackpoint: Elan TrackPoint firmware: 0x11, buttons: 3/3
    [    4.183050] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [    4.183053] Bluetooth: BNEP filters: protocol multicast
    [    4.183060] Bluetooth: BNEP socket layer initialized
    [    4.966475] Bluetooth: hci0: command 0x0c16 tx timeout
    [    4.966518] Bluetooth: hci0: sending frame failed (-19)
    [    6.986553] Bluetooth: hci0: command 0x2002 tx timeout
    [    6.987687] Bluetooth: hci0: sending frame failed (-19)
    [    8.998502] Bluetooth: hci0: command 0x2003 tx timeout
    [    8.998542] Bluetooth: hci0: sending frame failed (-19)
    [   11.014554] Bluetooth: hci0: command 0x201c tx timeout
    [   11.014600] Bluetooth: hci0: sending frame failed (-19)
    [   13.030511] Bluetooth: hci0: command 0x1002 tx timeout
    [   13.030637] Bluetooth: hci0: sending frame failed (-19)

```

---

