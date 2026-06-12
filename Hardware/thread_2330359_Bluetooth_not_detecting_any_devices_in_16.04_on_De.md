---
title: "Bluetooth not detecting any devices in 16.04 on Dell Inspiron"
date: 2016-07-11
forum: Hardware
---

### Post by Keen101 on 2016-07-11
My Bluetooth not detecting any devices, but otherwise say's it is working, but it doesent. Any tips on how to fix this as i would like to use my bluetooth headphones.

```
andrew@dell-Inspiron-3451:~$ lspci -knn | grep Net -A2; lsusb
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020e]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:575e Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0cf3:e005 Atheros Communications, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
andrew@dell-Inspiron-3451:~$ sudo bluetoothd -d -n
[sudo] password for andrew: 
bluetoothd[2958]: Bluetooth daemon 5.37
bluetoothd[2958]: src/main.c:parse_config() parsing main.conf
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'DiscoverableTimeout' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'PairableTimeout' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'AutoConnectTimeout' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'Name' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'Class' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'DeviceID' in group 'General'
bluetoothd[2958]: src/main.c:parse_config() Key file does not have key 'ReverseServiceDiscovery' in group 'General'
D-Bus setup failed: Name already in use
bluetoothd[2958]: Unable to get on D-Bus
```

---

