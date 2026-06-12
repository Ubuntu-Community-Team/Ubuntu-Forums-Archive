---
title: "No bluetooth found"
date: 2021-01-06
forum: Hardware
---

### Post by ankur6ue on 2021-01-06
Since yesterday (with no system changes on my part), bluetooth has stopped working on my Ubuntu 18.04 desktop. Here's the output of basic troubleshooting steps:

(base) ankur@master-node:~/dev/apps/ML$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

sudo systemctl restart bluetooth

systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
     Docs: man:bluetoothd(8)

Output of hciconfig is blank..

Can someone help please?

---

### Post by ankur6ue on 2021-01-06
Here's some more info..

(base) ankur@master-node:~/dev/apps/ML$ sudo modprobe btusb
(base) ankur@master-node:~/dev/apps/ML$ sudo systemctl start bluetooth.service
(base) ankur@master-node:~/dev/apps/ML$ systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Wed 2021-01-06 14:12:01 EST; 12s ago
     Docs: man:bluetoothd(8)
 Main PID: 17704 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;17704 /usr/lib/bluetooth/bluetoothd


Jan 06 14:12:01 master-node systemd[1]: Starting Bluetooth service...
Jan 06 14:12:01 master-node bluetoothd[17704]: Bluetooth daemon 5.50
Jan 06 14:12:01 master-node systemd[1]: Started Bluetooth service.
Jan 06 14:12:01 master-node bluetoothd[17704]: Starting SDP server
Jan 06 14:12:01 master-node bluetoothd[17704]: Version mismatch for sixaxis
Jan 06 14:12:01 master-node bluetoothd[17704]: Bluetooth management interface 1.

---

### Post by #&amp;thj^% on 2021-01-06
Check to see if it somehow got blacklisted.
```
sudo nano /etc/modprobe.d/blacklist.conf

```
Also look at:
```
lspci -knn | grep Net -A3; lsusb
```
Mine will show relevant "Intel Corp. Bluetooth wireless interface"
**EDIT:** With your new edit looks like its up now, can you now pair your device?

---

### Post by ankur6ue on 2021-01-06
Thanks for the response! Here's the output of sudo nano /etc/modprobe.d/blacklist.conf

and no, bluetooth still doesn't work



```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# Causes trackpads to stop working on Lenovo 11e 2nd gen (Ubuntu: #1802135)
# and Lenovo x240 to hang on boot (Ubuntu: #1802689)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

And 
```
(base) ankur@master-node:~/dev/apps/ML$ lspci -knn | grep Net -A3; lsusb
04:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter [1028:0310]
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci
16:02.0 PCI bridge [0604]: Intel Corporation Sky Lake-E PCI Express Root Port C [8086:2032] (rev 04)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 047f:02ee Plantronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 045e:0810 Microsoft Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 007: ID 187c:0526 Alienware Corporation 
Bus 001 Device 008: ID 045e:070f Microsoft Corp. LifeChat LX-3000 Headset
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by #&amp;thj^% on 2021-01-06
Yikes I see no BT device listed. :(
I'm _guessing_ firmware.
Just to see if any different, show this also please:
```
lsusb
```

---

### Post by ankur6ue on 2021-01-06
Here it is:
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 047f:02ee Plantronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 045e:0810 Microsoft Corp. 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 1058:0702 Western Digital Technologies, Inc. WD Passport (WDXMS)
Bus 001 Device 008: ID 187c:0526 Alienware Corporation 
Bus 001 Device 009: ID 045e:070f Microsoft Corp. LifeChat LX-3000 Headset
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ankur6ue on 2021-01-07
After running pillar to post and spending the whole day on this, turned out that all I needed was a cold reboot! Bluetooth works now. Thanks very much for all your suggestions!

---

