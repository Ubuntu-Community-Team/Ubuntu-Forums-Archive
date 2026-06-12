---
title: "bluetooth not working on Dell XPS 15 laptop with 18.04"
date: 2018-07-21
forum: Hardware
---

### Post by akos.maroy on 2018-07-21
Bluetooth doesn't work on the Dell XPS 15 laptop, with Ubuntu 18.04.

expected behavior:

in Settings, one goes to the Bluetooth tab, slides the 'ON' button to
'ON', and then Bluetooth is enabled, and one can pair devices

what is happening:

in Settings, when clicking on the 'ON' button in the Bluetooth tab, it
seems to turn on, that falls back to off

some relevant output:

```
$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetoothLinux
Linux dell-xps15 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
        Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
        Kernel driver in use: ath10k_pci
        Kernel modules: ath10k_pci
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0091 Validity Sensors, Inc. 
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0c45:6713 Microdia 
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    3.905518] Bluetooth: Core ver 2.22
[    3.905532] Bluetooth: HCI device and connection manager initialized
[    3.905534] Bluetooth: HCI socket layer initialized
[    3.905536] Bluetooth: L2CAP socket layer initialized
[    3.905539] Bluetooth: SCO socket layer initialized
[    0.028000] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.068684] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.460567] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    3.857792] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[    3.857799] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    3.860582] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.4.4.1-00079-QCARMSWPZ-1 api 6 features wowlan,ignore-otp crc32 fd869beb

```

any pointers to resolve this issue welcome

---

### Post by mIk3_08 on 2018-07-23
Did you already try to power on your bluetooth vai keyboard command.
its usually function key plus your wifi key.

---

