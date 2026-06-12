---
title: "intrepid ibex - dell internal bluetooth refuses to discover devices"
date: 2009-03-06
forum: Hardware
---

### Post by redline8400 on 2009-03-06
Hi all!  

I'm very new to all of this so please bear with me.

I've got an internal bluetooth module in my Dell Inspiron 6400 which won't detect my bluetooth devices.  I can switch it on and off, and the icon works, but it won't discover my devices.  (My bluetooth headset and phone were indeed set to discovery).  I just get to the "device search" page and nothing shows up.  I am running the 64 bit version of Ubuntu Intrepid 8.10.  Any suggestions as to what I might've done wrong?  Thanks for your help.

Pascal

---

### Post by orphzirra on 2009-03-17
I'm having the same problem.  Dell Inspiron 6000 running Ibex.  Blueman is managing bluetooth. When I place a Motorola H555 headset in pairing mode and scan with either the blueman applet or hcitool scan, it finds nothing.

lsusb output: 

Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth

```
$ hciconfig
hci0:	Type: USB
	BD Address: 00:10:C6:ED:C5:EA ACL MTU: 384:8 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:5042 acl:0 sco:0 events:284 errors:0
	TX bytes:1755 acl:0 sco:0 commands:165 errors:0

```

Here are the results from hcidump when running hcitool scan with headset in pair mode.

```
$ sudo hcidump
HCI sniffer - Bluetooth packet analyzer ver 1.42
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Inquiry (0x01|0x0001) plen 5
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Inquiry Complete (0x01) plen 1


```

---

