---
title: "bluetooth timeout"
date: 2011-10-15
forum: Hardware
---

### Post by chukchuck on 2011-10-15
I've a problem with Bluetooth...my notebook is** Sony Vaio VPCEH1S0E** and all works perfectly expect fro bluetooth.
Let's go.
I'm on **Ubuntu 11.10 64bit** and
**rfkill list **give me this:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```--------------------------------------------------------
**hcitool dev** give me this:
```
Devices:
```--------------------------------------------------------
**lsmod** give me this:
```
bluetooth             166112  13 bnep,rfcomm,btusb
```--------------------------------------------------------
**lsusb** give me this (for bluetooth):
```
Bus 001 Device 004: ID 0489:e027 Foxconn / Hon Hai 
```What can i do? :(

---

### Post by Simon Nuttall on 2011-10-17
Just adding that I have the same problem also on 64 bit 11.10 on a Sony VAIO VPCEJ have looked quite hard for suggestions but yet to find the answer.

---

