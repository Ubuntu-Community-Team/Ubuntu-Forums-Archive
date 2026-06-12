---
title: "Bluetooth not working (Asus 1005ha)"
date: 2011-01-11
forum: Hardware
---

### Post by bulva on 2011-01-11
Blueman assistant gives me a  "no adaptors found" message when trying to setup a device (nokia n900 running maemo), also hcitool dev lists no devices. However:


```
lsmod | grep bluetooth 
bluetooth              36327  6 rfcomm,sco,bnep,l2cap
rfkill                 10264  5 bluetooth,cfg80211,eeepc_laptop
```
Bluetooth service is running, device is enabled in bios settings.

---

