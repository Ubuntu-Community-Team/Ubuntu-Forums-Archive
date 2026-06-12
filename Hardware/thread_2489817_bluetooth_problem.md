---
title: "bluetooth problem"
date: 2023-08-10
forum: Hardware
---

### Post by hu016865 on 2023-08-10
I have a Sony svf1521bygb laptop
I installed Ubuntu 22.04 on it in uefi mode.
Bluetooth does not work by default.
With the following command, Bluetooth is activated,

```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd
```
 
but it does not search for any of the devices.
Previously, I had no problem with the above command on Ubuntu 18.04 and 19.10.

```
reza@reza-SVF1521BYGB:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 0489:e062 Foxconn / Hon Hai BCM43142A0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2717:5001 Xiaomi Inc. MI wireless mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
root@reza-SVF1521BYGB:/home/reza# sudo lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2717:5001 Xiaomi Inc. MI wireless mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.156427] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    8.249069] Bluetooth: Core ver 2.22
[    8.249117] NET: Registered PF_BLUETOOTH protocol family
[    8.249121] Bluetooth: HCI device and connection manager initialized
[    8.249130] Bluetooth: HCI socket layer initialized
[    8.249135] Bluetooth: L2CAP socket layer initialized
[    8.249143] Bluetooth: SCO socket layer initialized
[    8.654773] Bluetooth: hci0: BCM: chip id 70
[    8.655769] Bluetooth: hci0: BCM: features 0x06
[    8.671787] Bluetooth: hci0: reza-SVF1521BYGB
[    8.671797] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[    8.676651] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[    9.393916] Bluetooth: hci0: BCM: features 0x06
[    9.409785] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[    9.409793] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[   11.572308] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.572316] Bluetooth: BNEP filters: protocol multicast
[   11.572325] Bluetooth: BNEP socket layer initialized
[   11.579038] Bluetooth: MGMT ver 1.22
[   12.854306] Bluetooth: RFCOMM TTY layer initialized
[   12.854319] Bluetooth: RFCOMM socket layer initialized
[   12.854330] Bluetooth: RFCOMM ver 1.11
[  356.043057] Bluetooth: hci0: BCM: chip id 70
[  356.044051] Bluetooth: hci0: BCM: features 0x06
[  356.060059] Bluetooth: hci0: reza-SVF1521BYGB
[  356.060068] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  356.061123] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  356.791265] Bluetooth: hci0: BCM: features 0x06
[  356.808168] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  356.808191] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  356.870587] Bluetooth: MGMT ver 1.22
[  612.270264] Bluetooth: hci0: BCM: chip id 70
[  612.271261] Bluetooth: hci0: BCM: features 0x06
[  612.287272] Bluetooth: hci0: reza-SVF1521BYGB
[  612.287282] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  612.291330] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  613.015463] Bluetooth: hci0: BCM: features 0x06
[  613.032460] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  613.032484] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  613.094791] Bluetooth: MGMT ver 1.22
[  929.816956] Bluetooth: hci0: BCM: chip id 70
[  929.817927] Bluetooth: hci0: BCM: features 0x06
[  931.846730] Bluetooth: hci0: command 0x0c14 tx timeout
[  939.846502] Bluetooth: hci0: BCM: Reading local name failed (-110)
[  952.120606] Bluetooth: hci0: BCM: chip id 70
[  952.121585] Bluetooth: hci0: BCM: features 0x06
[  952.137611] Bluetooth: hci0: BCM43142A
[  952.137621] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[  952.138667] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  952.853802] Bluetooth: hci0: BCM: features 0x06
[  952.870749] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  952.870779] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  952.952343] Bluetooth: MGMT ver 1.22
[ 1016.822878] Bluetooth: hci0: BCM: chip id 70
[ 1016.823877] Bluetooth: hci0: BCM: features 0x06
[ 1016.839879] Bluetooth: hci0: reza-SVF1521BYGB
[ 1016.839888] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 1016.844960] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[ 1017.556023] Bluetooth: hci0: BCM: features 0x06
[ 1017.573066] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[ 1017.573095] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 1017.648455] Bluetooth: MGMT ver 1.22
root@reza-SVF1521BYGB:/home/reza# lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2717:5001 Xiaomi Inc. MI wireless mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.156427] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    8.249069] Bluetooth: Core ver 2.22
[    8.249117] NET: Registered PF_BLUETOOTH protocol family
[    8.249121] Bluetooth: HCI device and connection manager initialized
[    8.249130] Bluetooth: HCI socket layer initialized
[    8.249135] Bluetooth: L2CAP socket layer initialized
[    8.249143] Bluetooth: SCO socket layer initialized
[    8.654773] Bluetooth: hci0: BCM: chip id 70
[    8.655769] Bluetooth: hci0: BCM: features 0x06
[    8.671787] Bluetooth: hci0: reza-SVF1521BYGB
[    8.671797] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[    8.676651] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[    9.393916] Bluetooth: hci0: BCM: features 0x06
[    9.409785] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[    9.409793] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[   11.572308] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.572316] Bluetooth: BNEP filters: protocol multicast
[   11.572325] Bluetooth: BNEP socket layer initialized
[   11.579038] Bluetooth: MGMT ver 1.22
[   12.854306] Bluetooth: RFCOMM TTY layer initialized
[   12.854319] Bluetooth: RFCOMM socket layer initialized
[   12.854330] Bluetooth: RFCOMM ver 1.11
[  356.043057] Bluetooth: hci0: BCM: chip id 70
[  356.044051] Bluetooth: hci0: BCM: features 0x06
[  356.060059] Bluetooth: hci0: reza-SVF1521BYGB
[  356.060068] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  356.061123] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  356.791265] Bluetooth: hci0: BCM: features 0x06
[  356.808168] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  356.808191] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  356.870587] Bluetooth: MGMT ver 1.22
[  612.270264] Bluetooth: hci0: BCM: chip id 70
[  612.271261] Bluetooth: hci0: BCM: features 0x06
[  612.287272] Bluetooth: hci0: reza-SVF1521BYGB
[  612.287282] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  612.291330] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  613.015463] Bluetooth: hci0: BCM: features 0x06
[  613.032460] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  613.032484] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  613.094791] Bluetooth: MGMT ver 1.22
[  929.816956] Bluetooth: hci0: BCM: chip id 70
[  929.817927] Bluetooth: hci0: BCM: features 0x06
[  931.846730] Bluetooth: hci0: command 0x0c14 tx timeout
[  939.846502] Bluetooth: hci0: BCM: Reading local name failed (-110)
[  952.120606] Bluetooth: hci0: BCM: chip id 70
[  952.121585] Bluetooth: hci0: BCM: features 0x06
[  952.137611] Bluetooth: hci0: BCM43142A
[  952.137621] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[  952.138667] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  952.853802] Bluetooth: hci0: BCM: features 0x06
[  952.870749] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  952.870779] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  952.952343] Bluetooth: MGMT ver 1.22
[ 1016.822878] Bluetooth: hci0: BCM: chip id 70
[ 1016.823877] Bluetooth: hci0: BCM: features 0x06
[ 1016.839879] Bluetooth: hci0: reza-SVF1521BYGB
[ 1016.839888] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 1016.844960] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[ 1017.556023] Bluetooth: hci0: BCM: features 0x06
[ 1017.573066] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[ 1017.573095] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[ 1017.648455] Bluetooth: MGMT ver 1.22



```

old post in ubuntu 18.04 

[https://ubuntuforums.org/showthread.php?t=2437292&p=13933850#post13933850](https://ubuntuforums.org/showthread.php?t=2437292&p=13933850#post13933850)

---

### Post by #&amp;thj^% on 2023-08-10
To help us, with no fault of yours but show us this please:
```
rfkill list all
```
And a manual reboot or login has happened since you installed the firmware.
Now this as well:
```
lsmod | grep bluetooth

```
if it show something like below:
```
bluetooth            1036288  56 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth

```
Next pull up a terminal and run:
```
bluetoothctl power on
##And
bluetoothctl scan on
```
This might inspire someone to help you.
Dang i keep forgetting this>>>you need "bluez-alsa-utils" with that device.
And for me Pipewire/Wireplumber for bluetooth and sound helps on my devices. (Your mileage may vary though)

---

### Post by hu016865 on 2023-08-13
```
reza@reza-SVF1521BYGB:~$ rfkill list all0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```


```
reza@reza-SVF1521BYGB:~$ lsmod | grep bluetoothbluetooth            1036288  44 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth



```


```
reza@reza-SVF1521BYGB:~$ bluetoothctl power onChanging power on succeeded



```


```
reza@reza-SVF1521BYGB:~$ bluetoothctl scan onDiscovery started
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -90
[CHG] Device 70:FA:95:79:A1:68 RSSI: -92
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -85
[CHG] Device 70:FA:95:79:A1:68 RSSI: -86
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -92
[CHG] Device 70:FA:95:79:A1:68 RSSI: -89
[NEW] Device D0:D0:03:22:F0:8D D0-D0-03-22-F0-8D
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -83
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -87
[CHG] Device 70:FA:95:79:A1:68 RSSI: -86
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -83
[CHG] Device 70:FA:95:79:A1:68 RSSI: -88
[CHG] Device 70:FA:95:79:A1:68 RSSI: -88
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -84
[CHG] Device 70:FA:95:79:A1:68 RSSI: -88
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -85
[CHG] Device 70:FA:95:79:A1:68 RSSI: -86
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -95
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -87
[CHG] Device 70:FA:95:79:A1:68 RSSI: -83
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -84
[CHG] Device 70:FA:95:79:A1:68 RSSI: -92
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -83
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -88
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -86
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -93
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -87
[CHG] Device 70:FA:95:79:A1:68 RSSI: -82
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 70:FA:95:79:A1:68 RSSI: -83
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -93
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -92
[CHG] Device 70:FA:95:79:A1:68 RSSI: -87
[CHG] Device 62:7D:B9:D0:84:44 RSSI: -83
[CHG] Device 70:FA:95:79:A1:68 RSSI: -85
[NEW] Device 52:2B:5B:6E:D7:E1 52-2B-5B-6E-D7-E1
[DEL] Device D0:D0:03:22:F0:8D D0-D0-03-22-F0-8D
[DEL] Device 62:7D:B9:D0:84:44 62-7D-B9-D0-84-44
[DEL] Device 70:FA:95:79:A1:68 70-FA-95-79-A1-68
[DEL] Device 52:2B:5B:6E:D7:E1 52-2B-5B-6E-D7-E1



```

but bluetooth scan for device is empty

---

### Post by #&amp;thj^% on 2023-08-13
You forgot one:
```
apt policy bluez-alsa-utils
bluez-alsa-utils:
  Installed: 4.0.0-2
  Candidate: 4.0.0-2
  Version table:
 *** 4.0.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by hu016865 on 2023-08-14
```
apt policy bluez-alsa-utils bluez-alsa-utils:
  Installed: 3.0.0-2
  Candidate: 3.0.0-2
  Version table:
 *** 3.0.0-2 500
        500 http://archive.ubuntu.asiatech.ir jammy/universe amd64 Packages
        100 /var/lib/dpkg/status



```

---

### Post by hu016865 on 2023-08-14
when serach bkuetooth in my iphone i see loptop and connect to laptop but i laptop cant search other device .
why ?

---

### Post by #&amp;thj^% on 2023-08-14
> **hu016865 said:**
> when serach bkuetooth in my iphone i see loptop and connect to laptop but i laptop cant search other device .
why ?
Well that is why we we are looking, lets have a look here, paste back with Code tags:
```
sudo dmesg | grep -i 'blue'
```
I'm not sure a patch is needed now, but i may be wrong.

---

### Post by hu016865 on 2023-08-14
```
reza@reza-SVF1521BYGB:~$ sudo dmesg | grep -i 'blue'[sudo] password for reza: 
[    7.899501] Bluetooth: Core ver 2.22
[    7.899541] NET: Registered PF_BLUETOOTH protocol family
[    7.899545] Bluetooth: HCI device and connection manager initialized
[    7.899552] Bluetooth: HCI socket layer initialized
[    7.899556] Bluetooth: L2CAP socket layer initialized
[    7.899565] Bluetooth: SCO socket layer initialized
[    8.341735] Bluetooth: hci0: BCM: chip id 70
[    8.342895] Bluetooth: hci0: BCM: features 0x06
[    8.358746] Bluetooth: hci0: reza-SVF1521BYGB
[    8.358756] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[    8.363641] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[    9.099735] Bluetooth: hci0: BCM: features 0x06
[    9.116810] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[    9.116819] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[   11.215254] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.215263] Bluetooth: BNEP filters: protocol multicast
[   11.215270] Bluetooth: BNEP socket layer initialized
[   11.218282] Bluetooth: MGMT ver 1.22
[   11.542805] Bluetooth: RFCOMM TTY layer initialized
[   11.542819] Bluetooth: RFCOMM socket layer initialized
[   11.542830] Bluetooth: RFCOMM ver 1.11
[   11.593833] Bluetooth: hci0: Bad flag given (0x1) vs supported (0x0)



```

---

### Post by #&amp;thj^% on 2023-08-14
This is what I'm concerned with "BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch"
And here is why:"hci0: Bad flag given (0x1) vs supported (0x0)"
Admittedly I'm just not familiar enough with Sony, but I'm still on the fence for that patch?? (Weather it's needed now currently)
I have a meeting this afternoon with some Dev's i work with, will check back with any suggestion they offer.
And this might show more with a reissue of:
```
sudo modprobe -r btusb
sudo modprobe btusb
```
Check with:
```

dmesg | grep -i blu
```
A good return will look like this:
```
[  103.951150] Bluetooth: RFCOMM TTY layer initialized
[  103.951160] Bluetooth: RFCOMM socket layer initialized
[  103.951164] Bluetooth: RFCOMM ver 1.11

```
EDIT: After a talk with a friend this might need to be disabled:
```
systemctl status bluetooth-mesh.service
&#9675; bluetooth-mesh.service - Bluetooth mesh service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth-mesh.service; disabled;>
     Active: inactive (dead)

```

---

### Post by hu016865 on 2023-08-16
```
reza@reza-SVF1521BYGB:~$ sudo modprobe -r btusb reza@reza-SVF1521BYGB:~$ sudo modprobe btusb 
reza@reza-SVF1521BYGB:~$ sudo dmesg | grep -i blu
[    8.220688] Bluetooth: Core ver 2.22
[    8.220731] NET: Registered PF_BLUETOOTH protocol family
[    8.220734] Bluetooth: HCI device and connection manager initialized
[    8.220741] Bluetooth: HCI socket layer initialized
[    8.220745] Bluetooth: L2CAP socket layer initialized
[    8.220754] Bluetooth: SCO socket layer initialized
[   11.531065] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.531074] Bluetooth: BNEP filters: protocol multicast
[   11.531082] Bluetooth: BNEP socket layer initialized
[  640.028564] Bluetooth: hci0: BCM: chip id 70
[  640.029589] Bluetooth: hci0: BCM: features 0x06
[  640.045559] Bluetooth: hci0: BCM43142A
[  640.045569] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[  640.048517] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  640.777645] Bluetooth: hci0: BCM: features 0x06
[  640.793672] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  640.793699] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  640.858144] Bluetooth: MGMT ver 1.22
[  640.940916] Bluetooth: RFCOMM TTY layer initialized
[  640.940944] Bluetooth: RFCOMM socket layer initialized
[  640.940955] Bluetooth: RFCOMM ver 1.11
[  641.088854] Bluetooth: hci0: Bad flag given (0x1) vs supported (0x0)
[  661.192019] hid-generic 0005:0157:003D.0002: input,hidraw1: BLUETOOTH HID v1.01 Device [Mi Smart Band 5] on 0c:84:dc:f1:ee:12
[  709.623943] Bluetooth: hci0: BCM: chip id 70
[  709.624916] Bluetooth: hci0: BCM: features 0x06
[  709.640952] Bluetooth: hci0: reza-SVF1521BYGB
[  709.640961] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  709.646028] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  710.377175] Bluetooth: hci0: BCM: features 0x06
[  710.394067] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  710.394101] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  710.475656] Bluetooth: MGMT ver 1.22
[  710.622033] Bluetooth: hci0: Bad flag given (0x1) vs supported (0x0)
[  714.547699] hid-generic 0005:0157:003D.0003: input,hidraw1: BLUETOOTH HID v1.01 Device [Mi Smart Band 5] on 0c:84:dc:f1:ee:12
[  727.366405] hid-generic 0005:0157:003D.0004: input,hidraw1: BLUETOOTH HID v1.01 Device [Mi Smart Band 5] on 0c:84:dc:f1:ee:12
[  784.961291] Bluetooth: hci0: BCM: chip id 70
[  784.963268] Bluetooth: hci0: BCM: features 0x06
[  784.980266] Bluetooth: hci0: reza-SVF1521BYGB
[  784.980291] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  784.982581] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  785.705318] Bluetooth: hci0: BCM: features 0x06
[  785.722263] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  785.722292] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  785.804722] Bluetooth: MGMT ver 1.22
[  785.960296] Bluetooth: hci0: Bad flag given (0x1) vs supported (0x0)
[  789.792097] hid-generic 0005:0157:003D.0005: input,hidraw1: BLUETOOTH HID v1.01 Device [Mi Smart Band 5] on 0c:84:dc:f1:ee:12
[  841.817287] Bluetooth: hci0: urb 00000000f9bb3514 failed to resubmit (2)
[  850.830725] Bluetooth: hci0: BCM: chip id 70
[  850.832720] Bluetooth: hci0: BCM: features 0x06
[  850.849719] Bluetooth: hci0: reza-SVF1521BYGB
[  850.849743] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  850.851946] Bluetooth: hci0: BCM43142A0 'brcm/BCM43142A0-0489-e062.hcd' Patch
[  851.562724] Bluetooth: hci0: BCM: features 0x06
[  851.579655] Bluetooth: hci0: Broadcom Bluetooth Device (43142)
[  851.579680] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0280
[  851.649063] Bluetooth: MGMT ver 1.22



```



```
reza@reza-SVF1521BYGB:~$ sudo systemctl status bluetooth.service &#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Wed 2023-08-16 00:37:02 +0330; 14h ago
       Docs: man:bluetoothd(8)
   Main PID: 581 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 11680)
     Memory: 2.7M
        CPU: 797ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;581 /usr/lib/bluetooth/bluetoothd


&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
&#1575;&#1608;&#1578; 16 14:42:35 reza-SVF1521BYGB bluetoothd[581]: Endpoint registered: sender=:>
lines 1-22/22 (END)



```

---

### Post by #&amp;thj^% on 2023-08-16
That is just weird, and i assume your still not having any joy with bluetooth.
And jeremy31 had suggested this in your linked post on 18.04:
```
cd /lib/firmware/brcm
sudo mv BCM43142A0-0489-e062.hcd BCM.hcd
```
And a reboot.

All i can offer now is something like if the above don't work:
```
sudo rfkill unblock all 
sudo hciconfig hci0 down 
sudo rmmod btusb 
sudo modprobe btusb 
sudo hciconfig hci0 up
```
Good luck, I just can't see what is causing your problem.

---

### Post by hu016865 on 2023-09-01
I installed Kubuntu 23.04 and initially two packages:


sudo apt install dkms
apt install broadcom-sta-dkms


I installed
And then with the order
cd /lib/firmware/brcm
sudo wget [https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd](https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0489-e062.hcd)


I installed the bluetooth driver and the bluetooth is enabled.
But sometimes there is a sound interruption.
When I checked the system monitor, when playing music, sometimes the CPU suddenly increases without reason, and at this time the Bluetooth sound is cut off.
I checked with different players and saw that the definite difference is more in some. For example, vlc is less certain.
But if a program is running in the background, it will be more definite.
But if I close all the programs, the sound will be very low.
Does it have anything to do with the CPU?

---

