---
title: "problem with bluetooth"
date: 2020-02-21
forum: Hardware
---

### Post by hu016865 on 2020-02-21
i have sony vaio 1521 with ubuntu 19.10
my bluetooth wont work .
when i search for other devices it cant found any things
other devices cant find my sony vaio.
whth command : lspci :

```
SVF1521BYGB:~$ lspci00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

---

### Post by jeremy31 on 2020-02-21
Please post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by hu016865 on 2020-02-21
```
SVF1521BYGB:~$ lsusb; dmesg | egrep -i 'blue|firm'Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e062 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2717:5001 Xiaomi Inc. MI wireless mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.127765] Spectre V2 : Enabling Restricted Speculation for firmware calls
[   15.214596] Bluetooth: Core ver 2.22
[   15.214620] Bluetooth: HCI device and connection manager initialized
[   15.214624] Bluetooth: HCI socket layer initialized
[   15.214626] Bluetooth: L2CAP socket layer initialized
[   15.214631] Bluetooth: SCO socket layer initialized
[   15.630998] Bluetooth: hci0: BCM: chip id 70
[   15.631939] Bluetooth: hci0: BCM: features 0x06
[   15.647884] Bluetooth: hci0: BCM43142A
[   15.651882] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   15.711190] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0489-e062.hcd failed with error -2
[   15.711196] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0489-e062.hcd not found
[   33.931082] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.931088] Bluetooth: BNEP filters: protocol multicast
[   33.931105] Bluetooth: BNEP socket layer initialized
[   48.078101] Bluetooth: RFCOMM TTY layer initialized
[   48.078115] Bluetooth: RFCOMM socket layer initialized
[   48.078130] Bluetooth: RFCOMM ver 1.11
```

my laptop have internal bluetooth.
do i change command to lspci ?

---

### Post by hu016865 on 2020-02-21
lspci 

```
SVF1521BYGB:~$ lspci; dmesg | egrep -i 'blue|firm'00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
[    0.127765] Spectre V2 : Enabling Restricted Speculation for firmware calls
[   15.214596] Bluetooth: Core ver 2.22
[   15.214620] Bluetooth: HCI device and connection manager initialized
[   15.214624] Bluetooth: HCI socket layer initialized
[   15.214626] Bluetooth: L2CAP socket layer initialized
[   15.214631] Bluetooth: SCO socket layer initialized
[   15.630998] Bluetooth: hci0: BCM: chip id 70
[   15.631939] Bluetooth: hci0: BCM: features 0x06
[   15.647884] Bluetooth: hci0: BCM43142A
[   15.651882] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   15.711190] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0489-e062.hcd failed with error -2
[   15.711196] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0489-e062.hcd not found
[   33.931082] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.931088] Bluetooth: BNEP filters: protocol multicast
[   33.931105] Bluetooth: BNEP socket layer initialized
[   48.078101] Bluetooth: RFCOMM TTY layer initialized
[   48.078115] Bluetooth: RFCOMM socket layer initialized
[   48.078130] Bluetooth: RFCOMM ver 1.11

```

---

### Post by jeremy31 on 2020-02-21
It is missing firmware.  The bluetooth chipset is on the PCIe wifi card but seen as an USB device.  In terminal do
```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd
```
Shutdown and boot

---

### Post by hu016865 on 2020-02-21
tnx alot ...
sloved...

---

### Post by hu016865 on 2020-02-21
i do it in ubuntu 18.04 and dont work ..

```
SVF1521BYGB:~$ lsusb; dmesg | egrep -i 'blue|firm'Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:e062 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2717:5001  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.033558] Spectre V2 : Enabling Restricted Speculation for firmware calls
[   26.577172] Bluetooth: Core ver 2.22
[   26.577192] Bluetooth: HCI device and connection manager initialized
[   26.577196] Bluetooth: HCI socket layer initialized
[   26.577198] Bluetooth: L2CAP socket layer initialized
[   26.577204] Bluetooth: SCO socket layer initialized
[   27.609819] Bluetooth: hci0: BCM: chip id 70
[   27.610787] Bluetooth: hci0: BCM: features 0x06
[   27.626793] Bluetooth: hci0: BCM43142A
[   27.626797] Bluetooth: hci0: BCM (001.001.011) build 0000
[   27.671710] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   27.671714] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   29.696141] Bluetooth: hci0: command 0x1003 tx timeout
[   29.697917] Bluetooth: hci0: unexpected event for opcode 0x1003
[   35.970260] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.970264] Bluetooth: BNEP filters: protocol multicast
[   35.970271] Bluetooth: BNEP socket layer initialized
[   38.624153] Bluetooth: hci0: command 0x1003 tx timeout
[   38.625902] Bluetooth: hci0: unexpected event for opcode 0x1003
[   53.453355] Bluetooth: RFCOMM TTY layer initialized
[   53.453378] Bluetooth: RFCOMM socket layer initialized
[   53.453388] Bluetooth: RFCOMM ver 1.11
[   86.813194] Bluetooth: hci0: BCM: chip id 70
[   86.814134] Bluetooth: hci0: BCM: features 0x06
[   86.830184] Bluetooth: hci0: reza-SVF1521BYGB
[   86.830196] Bluetooth: hci0: BCM (001.001.011) build 0000
[   86.830241] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   86.830247] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  134.958229] Bluetooth: hci0: BCM: chip id 70
[  134.959226] Bluetooth: hci0: BCM: features 0x06
[  134.975242] Bluetooth: hci0: reza-SVF1521BYGB
[  134.975248] Bluetooth: hci0: BCM (001.001.011) build 0000
[  134.975266] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  134.975269] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  136.991599] Bluetooth: hci0: command 0x1003 tx timeout
[  136.993220] Bluetooth: hci0: unexpected event for opcode 0x1003
```

---

### Post by jeremy31 on 2020-02-21
```
cd /lib/firmware/brcm
sudo mv BCM43142A0-0489-e062.hcd BCM.hcd
```
Reboot

---

### Post by hu016865 on 2020-02-21
after reboot worked ok ..
tnx again.

---

