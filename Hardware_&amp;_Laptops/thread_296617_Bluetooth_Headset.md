---
title: "Bluetooth Headset"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by etaham on 2006-11-09
I'm having trouble pairing my bluetooth headset with my computer.  when i enter 'sudo hcitool cc 00:03:89:7B:A7:66' get:
```
Can't create connection: Input/output error
```
I have searched all over for a solution. I am running edgy. There was talk about a special applet that should load and request a pin.  I've never seen it. Anyone have any idea? 
can someone paste me their /etc/bluetooth/hcid.conf so i can compare it to mine?

Thanks
etaham

SOLUTION:
run bt-applet. thats the new applet. run it then try to connect.

---

