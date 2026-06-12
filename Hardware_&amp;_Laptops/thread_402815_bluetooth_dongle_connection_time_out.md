---
title: "bluetooth dongle connection time out"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by quirks on 2007-04-06
Hi all!

I am trying to get a bluetooth USB dongle to work in Xubuntu Edgy. I followed the procedure described in [https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup") and got to the point where you scan for other bluetooth devices using [FONT="Courier New"]hidd --search[/FONT] or [FONT="Courier New"]hcitool scan[/FONT].

However, none of them works. Instead I always get a connection timeout. Searching the forum, I found a hint to run [FONT="Courier New"]hciconfig hci0 reset[/FONT], but that didn't work either.

Here is some output that might be helpful (all commands were run as root):

```
# lsusb
Bus 001 Device 017: ID 0400:0807 National Semiconductor Corp. Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000
```

```
# hcitool dev
Devices:
        hci0    08:00:17:1D:D6:8A
```

```
# hciconfig -a
hci0:   Type: USB
        BD Address: 08:00:17:1D:D6:8A ACL MTU: 339:4 SCO MTU: 64:9
        UP RUNNING 
        RX bytes:45 acl:0 sco:0 events:4 errors:0
        TX bytes:6 acl:0 sco:0 commands:13 errors:0
        Features: 0xff 0x3b 0x05 0x00 0x00 0x00 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)
```

```
# hidd --search
Searching ...
```

```
# hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

```
# hciconfig hci0 inqmode 0
Can't set inquiry mode on hci0: Connection timed out (110)
```

```
# hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
```

I know things like these are ugly and I don't believe anymore that I will get it to work, but any help is appreciated. Also, if you need any further information, just ask.

Thanks,
quirks

---

### Post by ensenadaubuntulover on 2007-05-16
bottom line

bluetooth does NOT work on edgy eft

---

