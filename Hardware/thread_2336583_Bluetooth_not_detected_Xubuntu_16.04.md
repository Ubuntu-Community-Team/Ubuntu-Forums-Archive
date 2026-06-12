---
title: "Bluetooth not detected Xubuntu 16.04"
date: 2016-09-09
forum: Hardware
---

### Post by Lawand on 2016-09-09
I have a Asus laptop R556L and I installed Xubuntu 16.04 and the bluetooth is not detected.

Running bluetooth manager shows:

```
Bluez daemon is not running, blueman-manager cannot continue.
This probably means that there were no Bluetooth adapters detected or Bluetooth daemon was not started.
```

Running "ps -ef | grep blue" shows:

```
lawand    3527  3501  0 23:47 ?        00:00:00 /usr/bin/python3 /usr/bin/blueman-applet
lawand    3845  3185  0 23:47 ?        00:00:00 /usr/lib/bluetooth/obexd
lawand    5907  3625  0 23:57 ?        00:00:00 /usr/bin/python3 /usr/bin/blueman-manager
lawand    5917  3185  0 23:57 ?        00:00:00 /usr/bin/python3 /usr/bin/blueman-adapters
lawand    5949  5929  0 23:58 pts/1    00:00:00 grep --color=auto blue
```

Running "lspci -knn | grep Net -A2; lsusb" shows:

```
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave AW-NE186H [1a3b:1186]
	Kernel driver in use: ath9k
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I tried purging "blueman bluez-utils bluez bluetooth" and install them again but that didn't work.

I checked "sudo rfkill list":

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

Any ideas? Thanks.

---

### Post by jeremy31 on 2016-09-10
You may have the Atheros AR5B125 card that doesn't include bluetooth as there isn't a bluetooth device listed in your lsusb results.  I have a AR5B225 in my Lenovo and it has the same AR9485 wireless chip with bluetooth

---

### Post by gordintoronto on 2016-09-10
IMHO, the best hardware description is produced by these two commands:
cd Desktop
sudo lshw -html > config.htm

config.htm should appear on your desktop, and when you double-click it, it opens in your browser. Then you can search for "blue" and I suspect it will not be found.

---

### Post by Lawand on 2016-09-11
yeah, i guess there's no embedded bluetooth adapter. I tried using lshw and i indeed can't find anything there. thanks guys for the help!

---

