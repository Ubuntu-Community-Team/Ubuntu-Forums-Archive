---
title: "On four USB ports, 1 unrecognized, then 2"
date: 2018-11-24
forum: Hardware
---

### Post by v-squiggle on 2018-11-24
I have 4 USB ports
[LIST=1]
[*]Anker multiport that works 
[*]This port is the first one that has stopped working 
[*]Logitech keyboard and mouse 
[*]This port has just stopped working. 
[/LIST]
It seems that under Windows, there is a utility that "empty" the data that has not been purged and that blocks a USB port. I do not see anything like that in Linux

The lsusb command gives

```

Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0bda:57ed Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 04e8:3469 Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 046d:0a07 Logitech, Inc. Z-10 Speakers
Bus 001 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any idea how to proceed ?

(I'm on VOYAGER 18.04 LTS // Asus Gris R516UB-DM044T - 15,6'' Full HD - Intel  Core i7-6500U - HDD 1 To + SSD 128 Go - RAM 8 Go - NVIDIA GeForce 940M 2  Go)

---

