---
title: "USB dongle bluetooth doen't work"
date: 2011-04-23
forum: Hardware
---

### Post by MaikoID on 2011-04-23
Hi, I'm trying to use my usb dongle but I've tried everything that I found on Google and in this forum and nothing. 

Gnome recognize my dongle because if I remove/put it the icon appears but doesn't work, if I try to add new device it tries to find one forever and returns me nothing.

LSUB
```

root@maiko-notelinux:~# lsusb
Bus 002 Device 003: ID 1532:0013 Razer USA, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg - the last message
```

[ 6867.352930] hci_cmd_task: hci0 command tx timeout

```

hciconfig
```

root@maiko-notelinux:~# hciconfig 
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:01:1C  ACL MTU: 1021:4  SCO MTU: 180:1
	UP RUNNING 
	RX bytes:322 acl:0 sco:0 events:7 errors:0
	TX bytes:21 acl:0 sco:0 commands:19 errors:12



```

hciconfig -a
```

root@maiko-notelinux:~# hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:01:1C  ACL MTU: 1021:4  SCO MTU: 180:1
	UP RUNNING 
	RX bytes:322 acl:0 sco:0 events:7 errors:0
	TX bytes:21 acl:0 sco:0 commands:19 errors:12
	Features: 0xff 0x3e 0x09 0x76 0x80 0x01 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)


```

hcitool scan

```
root@maiko-notelinux:~# hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

hcitool dev
```

root@maiko-notelinux:~# hcitool dev
Devices:
	hci0	00:1F:81:00:01:1C


```



Thx for any help

Edit: After reboot I change the usb port and now its working

---

### Post by ethan1701 on 2011-09-02
I had the same exact issue with the bluetooth dongle I bought on DealExtreme (SKU 11866 [http://www.dealextreme.com/sku.aspx?sku=11866&urlrewritetitle=super-mini-bluetooth-2-0-adapter-dongle-vista-compatible~r.55113731](http://www.dealextreme.com/sku.aspx?sku=11866&urlrewritetitle=super-mini-bluetooth-2-0-adapter-dongle-vista-compatible~r.55113731)).
I was going crazy trying to get it to work.
I tried every USB port on my computer, but nothing worked. I had given up hope when I read this: [http://www.digifail.com/hardware/dxdevices.shtml](http://www.digifail.com/hardware/dxdevices.shtml)
But after stumbling upon this post, I got it to work by rebooting the computer, and switching the port it was plugged into.

It might not be the best bluetooth dongle out there, but it does the job.

-Ethan

---

