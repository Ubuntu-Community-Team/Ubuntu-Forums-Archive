---
title: "Gateway LT2104u Card Reader"
date: 2010-08-23
forum: Hardware
---

### Post by Sallée on 2010-08-23
Cannot get my card reader to show anything.  The card seems to be recognized, I just cannot find out how to get to it.  Please help.  Thanks in advance.
[LIST]
[*]No option to disconnect through BIOS, as some posts have suggested.  
[*]I would really prefer not to open the case if I can avoid it, as another post suggested.  
[*]Booting with card inserted made no difference.
[*]Do not see any possibilities in /dev/disk.
[*]No recognition in gparted. 
[/LIST]

Results without SD card inserted:
```
j@A:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
j@A:~$ dmesg | tail
[  102.454015] wlan0: associate with 00:1c:df:d0:07:0e (try 1)
[  102.456945] wlan0: RX AssocResp from 00:1c:df:d0:07:0e (capab=0x411 status=0 aid=3)
[  102.456962] wlan0: associated
[  102.458199] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  112.776589] wlan0: no IPv6 routers present
[  113.847979] lo: Disabled Privacy Extensions
[  376.314963] usb 1-5: USB disconnect, address 3
[  410.400117] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  410.533978] usb 1-5: configuration #1 chosen from 1 choice
[  625.767860] usb 1-5: USB disconnect, address 4
```

Results of SD card:

```
j@A:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0cf2:6250 ENE Technology, Inc. 
Bus 001 Device 002: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
j@A:~$ dmesg | tail
[  102.456962] wlan0: associated
[  102.458199] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  112.776589] wlan0: no IPv6 routers present
[  113.847979] lo: Disabled Privacy Extensions
[  376.314963] usb 1-5: USB disconnect, address 3
[  410.400117] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  410.533978] usb 1-5: configuration #1 chosen from 1 choice
[  625.767860] usb 1-5: USB disconnect, address 4
[  756.124108] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  756.257865] usb 1-5: configuration #1 chosen from 1 choice

```

---

### Post by devildogmech on 2010-10-01
Same Problem with the same system here. Anyone have an answer?

---

### Post by avacado on 2010-10-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

---

### Post by Sallée on 2011-12-03
Fixed on upgrade to 11.10

---

