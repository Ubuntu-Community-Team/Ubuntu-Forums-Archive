---
title: "Weird bluetooth behavior on 9.04 and jaunty"
date: 2009-05-12
forum: Hardware
---

### Post by tdi on 2009-05-12
I Upgraded to jaunty on my dell d430. My bluetooth is present there, hciconfig show the dongle:

```
hci0:    Type: USB
    BD Address: 00:1A:6B:FB:F1:31 ACL MTU: 310:10 SCO MTU: 64:8
    UP RUNNING 
    RX bytes:351 acl:0 sco:0 events:12 errors:0
    TX bytes:43 acl:0 sco:0 commands:11 errors:0
```

But issuing the hcitool scan command returns nothing. Also the adapter is not discovered by BT enabled phones that is successfully used with 8.04. Dmesg shows nothing particular weird. 

My system.
lsusb:
Bus 002 Device 009: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth

---

### Post by DonA on 2009-07-31
Sorry, this isn't a fix.  Rather, it's a "me too".

Running Jaunty on a Dell 1505N.

'lsusb' shows my Dell 355 Bluetooth interface.

I can pair with each of my BT headsets, but 
'hcitool scan' doesn't show them.  (It does show my wife's MacBook though.)

Grasping at straws, I installed 'blueman', but no change in hcitool scan results.

Puzzled.

..DonA

---

