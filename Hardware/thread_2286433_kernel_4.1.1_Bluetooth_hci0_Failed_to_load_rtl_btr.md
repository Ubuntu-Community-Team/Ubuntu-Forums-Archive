---
title: "kernel 4.1.1: Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin"
date: 2015-07-12
forum: Hardware
---

### Post by sanderj on 2015-07-12
I installed linux kernel 4.1.1 on my Ubuntu 15.04 (trying to get rid of some problems). My dmesg now says:

```
[   11.275915] Bluetooth: Core ver 2.20
[   11.275978] NET: Registered protocol family 31
[   11.275980] Bluetooth: HCI device and connection manager initialized
[   11.275989] Bluetooth: HCI socket layer initialized
[   11.275993] Bluetooth: L2CAP socket layer initialized
[   11.276019] Bluetooth: SCO socket layer initialized
[   11.313264] usbcore: registered new interface driver btusb
[   11.316676] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   11.316679] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   11.316721] usb 1-4.3: Direct firmware load for rtl_bt/rtl8723b_fw.bin failed with error -2
[   11.316723] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin
```

Indeed there is no file rtl8723b_fw.bin on my system. I do have:


```
$ locate rtl8723 | grep -i firmware
/lib/firmware/rtlwifi/rtl8723aufw_A.bin
/lib/firmware/rtlwifi/rtl8723aufw_B.bin
/lib/firmware/rtlwifi/rtl8723aufw_B_NoBT.bin
/lib/firmware/rtlwifi/rtl8723befw.bin
/lib/firmware/rtlwifi/rtl8723fw.bin
/lib/firmware/rtlwifi/rtl8723fw_B.bin
```

The bluetooth logo has a red cross in it. 

Tips appreciated how to solve this.

---

### Post by jeremy31 on 2015-07-12
You will likely need to download linux-firmware from a mirror site listed [http://packages.ubuntu.com/wily/all/linux-firmware/download](http://packages.ubuntu.com/wily/all/linux-firmware/download) and install

---

### Post by sanderj on 2015-07-12
I did that (see below), and the dmesg error message is gone. Thank you!

(Bluetooth is still not working, but that was also the case on 3.19 ... :(  )


```
$ sudo dpkg -i  linux-firmware_1.145_all.deb

(Reading database ... 428678 files and directories currently installed.)
Preparing to unpack linux-firmware_1.145_all.deb ...
Unpacking linux-firmware (1.145) over (1.143.1) ...
Setting up linux-firmware (1.145) ...

$ sudo updatedb
$ locate rtl8723b_fw.bin
/lib/firmware/rtl_bt/rtl8723b_fw.bin


```
After a reboot:

```

$ dmesg | grep -i bluetooth
[   10.500242] usb 1-4.3: Product: Bluetooth Radio 
[   11.197880] Bluetooth: Core ver 2.20
[   11.197905] Bluetooth: HCI device and connection manager initialized
[   11.197911] Bluetooth: HCI socket layer initialized
[   11.197915] Bluetooth: L2CAP socket layer initialized
[   11.197924] Bluetooth: SCO socket layer initialized
[   11.226482] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   11.226484] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   11.238214] Bluetooth: hci0: rom_version status=0 version=1
[   14.079555] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.079560] Bluetooth: BNEP filters: protocol multicast
[   14.079568] Bluetooth: BNEP socket layer initialized
[   14.144210] Bluetooth: RFCOMM TTY layer initialized
[   14.144225] Bluetooth: RFCOMM socket layer initialized
[   14.144236] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2015-07-12
```
rfkill list all; hciconfig -a
```

Pilot6's PPA should work on the 3.19 kernel if nothing else works, see his answer [http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices](http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices)

---

### Post by sanderj on 2015-07-12
```
$ rfkill list all; hciconfig -a
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
hci0:	Type: BR/EDR  Bus: USB
	BD Address: AC:D1:B8:1A:1C:FC  ACL MTU: 820:8  SCO MTU: 255:16
	UP RUNNING PSCAN 
	RX bytes:2404 acl:0 sco:0 events:167 errors:0
	TX bytes:23964 acl:0 sco:0 commands:166 errors:0
	Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'RTK_BT_4.0'
	Class: 0x000000
	Service Classes: Unspecified
	Device Class: Miscellaneous, 
	HCI Version: 4.0 (0x6)  Revision: 0xb
	LMP Version: 4.0 (0x6)  Subversion: 0x8723
	Manufacturer: Realtek Semiconductor Corporation (93)
```


```
sander@superstreamer:~$ hcitool scan
Scanning ...

sander@superstreamer:~$ bt-device -l
No devices found

sander@superstreamer:~$ hciconfig scan
hci0:	Type: BR/EDR  Bus: USB
	BD Address: AC:D1:B8:1A:1C:FC  ACL MTU: 820:8  SCO MTU: 255:16
	UP RUNNING PSCAN 
	RX bytes:2404 acl:0 sco:0 events:167 errors:0
	TX bytes:23964 acl:0 sco:0 commands:166 errors:0


```

---

