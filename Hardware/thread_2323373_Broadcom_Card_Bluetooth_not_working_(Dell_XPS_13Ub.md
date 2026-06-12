---
title: "Broadcom Card Bluetooth not working (Dell XPS 13/Ubuntu 16.04)"
date: 2016-05-04
forum: Hardware
---

### Post by Vonologic on 2016-05-04
So after setting up the wi-fi for my Broadcom 4352, I attempted to setup bluetooth by installing Blueman and all of its dependencies. However, blueman would display the bluetooth devices around, but when I tried to pair I would just get "Failed to add device." In an attempt to fix this, I decided to reinstall Blueman, but now I simply don't see the devices at all. I'm running XFCE on Ubuntu 16.04, and the wireless card in question is a Broadcom 4352, which is the card in my Dell XPS 13.

The output of lsusb shows the device:
```
Bus 001 Device 002: ID 8087:8001 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:5682 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
Bus 002 Device 002: ID 18d1:4ee2 Google Inc. Nexus 4 (debug)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

(Not sure why it displays my Nexus 6P as a Nexus 4, but that's irrelevant :P)

Also here are the files in my /lib/firmware/brcm if it helps: 
```
bcm4329-fullmac-4.bin   brcmfmac43241b0-sdio.bin  brcmfmac43340-sdio.bin  brcmfmac4350c2-pcie.bin  brcmfmac43602-pcie.ap.binbcm43xx-0.fw            brcmfmac43241b4-sdio.bin  brcmfmac4334-sdio.bin   brcmfmac4350-pcie.bin    brcmfmac43602-pcie.bin
bcm43xx_hdr-0.fw        brcmfmac43241b5-sdio.bin  brcmfmac4335-sdio.bin   brcmfmac4354-sdio.bin    brcmfmac4366b-pcie.bin
brcmfmac43143.bin       brcmfmac43242a.bin        brcmfmac43362-sdio.bin  brcmfmac43569.bin        brcmfmac4371-pcie.bin
brcmfmac43143-sdio.bin  brcmfmac4329-sdio.bin     brcmfmac4339-sdio.bin   brcmfmac4356-pcie.bin
brcmfmac43236b.bin      brcmfmac4330-sdio.bin     brcmfmac43455-sdio.bin  brcmfmac43570-pcie.bin



```

I have tried resetting my bluetooth as well, to no avail. Any advice would be appreciated, so thank you in advance!

EDIT: More info:
```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetoothLinux davon-XPS-13-9343 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
	Kernel driver in use: wl
	Kernel modules: bcma, wl
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:5682 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
Bus 002 Device 002: ID 18d1:4ee2 Google Inc. Nexus 4 (debug)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.041983] Bluetooth: Core ver 2.21
[    2.042001] Bluetooth: HCI device and connection manager initialized
[    2.042006] Bluetooth: HCI socket layer initialized
[    2.042009] Bluetooth: L2CAP socket layer initialized
[    2.042015] Bluetooth: SCO socket layer initialized
[    2.059636] Bluetooth: hci0: BCM: chip id 63
[    2.076857] Bluetooth: hci0: ChromeLinux_851B
[    2.078706] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    2.080403] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-216f.hcd failed with error -2
[    2.080407] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-216f.hcd not found
[    3.123084] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.123087] Bluetooth: BNEP filters: protocol multicast
[    3.123091] Bluetooth: BNEP socket layer initialized
[    4.066328] Bluetooth: RFCOMM TTY layer initialized
[    4.066349] Bluetooth: RFCOMM socket layer initialized
[    4.066361] Bluetooth: RFCOMM ver 1.11
[    2.080403] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-216f.hcd failed with error -2
bluetooth             520192  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel



```

---

### Post by jeremy31 on 2016-05-04
Looks to be a firmware issue
```
wget https://www.dropbox.com/s/r2pb41rhx65t9zi/BCM20702A0-0a5c-216f.hcd
sudo cp BCM20702A0-0a5c-216f.hcd /lib/firmware/brcm/BCM20702A1-0a5c-216f.hcd
```

Reboot

---

### Post by Vonologic on 2016-05-04
> **jeremy31 said:**
> Looks to be a firmware issue
```
wget https://www.dropbox.com/s/r2pb41rhx65t9zi/BCM20702A0-0a5c-216f.hcd
sudo cp BCM20702A0-0a5c-216f.hcd /lib/firmware/brcm/BCM20702A1-0a5c-216f.hcd
```

Reboot

Thanks, got it working after this. Although I don't see my headphones as an audio option yet, which is probably a seperate issue. Shoudl I be pairing as an "Audio sink" or "Headset?"

---

### Post by jeremy31 on 2016-05-04
Audio sink may give you better sound if A2DP is mentioned, Headset is usually low quality audio and mainly used for phone calls.  You should check ```
pactl list short | grep bluetooth
``` to see if module-bluetooth-discover is in the results

If you don't see module-bluetooth-discover in the results then ```
pactl load-module module-bluetooth-discover
```  Then you may have to delete the pairing and pair again for the changes to take affect

---

### Post by Vonologic on 2016-05-04
> **jeremy31 said:**
> Audio sink may give you better sound if A2DP is mentioned, Headset is usually low quality audio and mainly used for phone calls.  You should check ```
pactl list short | grep bluetooth
``` to see if module-bluetooth-discover is in the results

If you don't see module-bluetooth-discover in the results then ```
pactl load-module module-bluetooth-discover
```  Then you may have to delete the pairing and pair again for the changes to take affect

module-bluetooth-discover is listed. I paired it on "Audio Sink" successfully, I just don't see it in PulseAudio when I look under Playback devices.

---

### Post by jeremy31 on 2016-05-04
Strange as it sound show in Sound Settings under output

---

### Post by Vonologic on 2016-05-06
> **jeremy31 said:**
> Strange as it sound show in Sound Settings under output

So according to bluetoothctl, when I connect the headphones, they immediately disconnect (which naturally doesn't allow me to see them under the sound settings)

```
davon@davon-XPS-13-9343:~$ bluetoothctl[NEW] Controller C4:8E:8F:F8:12:8E ChromeLinux_851B [default]
[NEW] Device 44:5E:F3:B3:2C:48 Jaybird X2
**[CHG] Device 44:5E:F3:B3:2C:48 Connected: yes**
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 000080ff-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 Paired: yes
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x14010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x10010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
**[CHG] Device 44:5E:F3:B3:2C:48 Connected: no**
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x18010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x1c010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
```

Everytime I reset the headphones, I see the same result, connected and immediately unconnected.

---

### Post by Vonologic on 2016-05-13
So I'm trying to connect my Jaybird X2 headphones to my laptop, which is running Ubuntu 16.04. When I connect the headphones via blueman, the device is added successfully but fails to connect. However, I hear the connected sound and then the disconnected sound through the headphones everytime, so I know there is a brief (1-2 seconds) period that the headphones are connected. Obviously, since they don't stay connected for long enough I cannot use them as an audio source. Can anyone help me figure out why they won't stay connected? Here is my bluetoothctl (pulled from my[ previous thread]("http://ubuntuforums.org/showthread.php?t=2323373")):
```

davon@davon-XPS-13-9343:~$ bluetoothctl[NEW] Controller C4:8E:8F:F8:12:8E ChromeLinux_851B [default]
[NEW] Device 44:5E:F3:B3:2C:48 Jaybird X2
**[CHG] Device 44:5E:F3:B3:2C:48 Connected: yes**
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 UUIDs: 000080ff-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 Paired: yes
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x14010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x10010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
**[CHG] Device 44:5E:F3:B3:2C:48 Connected: no**
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x18010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x1c010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb 
```

---

### Post by jeremy31 on 2016-05-14
In  terminal with ```
bluetoothctl
```
Trust the device with ```
trust 44:5E:F3:B3:2C:48
``` and then see if it will stay connected with ```
connect 44:5E:F3:B3:2C:48
```

---

### Post by bapoumba on 2016-05-14
Threads merged.

---

### Post by Vonologic on 2016-05-14
> **bapoumba said:**
> Threads merged.

Thank you!

> **jeremy31 said:**
> In terminal with ```
bluetoothctl
```
Trust the device with ```
trust 44:5E:F3:B3:2C:48
``` and then see if it will stay connected with ```
connect 44:5E:F3:B3:2C:48
```

Still does not work unfortunately. I believe it was already trusted. Here's the output:
```
bluetoothctl[NEW] Controller C4:8E:8F:F8:12:8E ChromeLinux_851B [default]
[NEW] Device 88:C6:26:55:A4:9D UE ROLL
[NEW] Device 44:5E:F3:B3:2C:48 Jaybird X2
[bluetooth]# trust 44:5E:F3:B3:2C:48
[CHG] Device 44:5E:F3:B3:2C:48 Trusted: yes
Changing 44:5E:F3:B3:2C:48 trust succeeded
[bluetooth]# connect 44:5E:F3:B3:2C:48
Attempting to connect to 44:5E:F3:B3:2C:48
[CHG] Device 44:5E:F3:B3:2C:48 Connected: yes
Failed to connect: org.bluez.Error.Failed
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x14010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x10010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Device 44:5E:F3:B3:2C:48 Connected: no
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x18010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E Class: 0x1c010c
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001106-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001104-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00005005-0000-1000-8000-0002ee000001
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001133-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Controller C4:8E:8F:F8:12:8E UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[bluetooth]# 

```

---

### Post by jeremy31 on 2016-05-14
Lets see ```
systemctl status bluetooth
```

---

### Post by Vonologic on 2016-05-14
> **jeremy31 said:**
> Lets see ```
systemctl status bluetooth
```

So it just connected and its working perfectly all of a sudden...not sure how long this is gonna last. But just in case it doesn't, here were the results:

```
&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2016-05-09 19:47:38 EDT; 4 days ago
     Docs: man:bluetoothd(8)
 Main PID: 905 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 512)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;905 /usr/lib/bluetooth/bluetoothd


May 14 14:16:34 davon-XPS-13-9343 bluetoothd[905]: Unable to register GATT service with handle 0x0001 for device 88:C6:26:55:A4:9D
May 14 14:21:35 davon-XPS-13-9343 bluetoothd[905]: Unable to register GATT service with handle 0x0001 for device 88:C6:26:55:A4:9D
May 14 14:25:05 davon-XPS-13-9343 bluetoothd[905]: Endpoint unregistered: sender=:1.495 path=/MediaEndpoint/A2DPSource
May 14 14:25:05 davon-XPS-13-9343 bluetoothd[905]: Endpoint unregistered: sender=:1.495 path=/MediaEndpoint/A2DPSink
May 14 14:25:10 davon-XPS-13-9343 bluetoothd[905]: Endpoint registered: sender=:1.505 path=/MediaEndpoint/A2DPSource
May 14 14:25:10 davon-XPS-13-9343 bluetoothd[905]: Endpoint registered: sender=:1.505 path=/MediaEndpoint/A2DPSink
May 14 14:25:26 davon-XPS-13-9343 bluetoothd[905]: connect error: Connection timed out (110)
May 14 14:25:29 davon-XPS-13-9343 bluetoothd[905]: GLib: Source ID 7574 was not found when attempting to remove it
May 14 14:25:29 davon-XPS-13-9343 bluetoothd[905]: /org/bluez/hci0/dev_44_5E_F3_B3_2C_48/fd3: fd(37) ready
May 14 14:25:29 davon-XPS-13-9343 bluetoothd[905]: Control: Refusing unexpected connect



```

88:C6:26:55:A4:9D is the address of another bluetooth speaker I own (that works perfectly) but is powered off

---

