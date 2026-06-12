---
title: "Bluetooth troubles with HP DV9000"
date: 2009-01-02
forum: Hardware
---

### Post by earthmeLon on 2009-01-02
I am having trouble getting my bluetooth device working.

I am using an [HP Pavillion DV9000]("http://h10025.www1.hp.com/ewfrf/wc/product?product=1842189&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us")

```
dmesg | grep Bluetooth
[ 27.685501] Bluetooth: Core ver 2.13
[ 27.686022] Bluetooth: HCI device and connection manager initialized
[ 27.686029] Bluetooth: HCI socket layer initialized
[ 27.717324] Bluetooth: L2CAP ver 2.11
[ 27.717334] Bluetooth: L2CAP socket layer initialized
[ 27.736989] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 27.737008] Bluetooth: BNEP filters: protocol multicast
[ 27.788186] Bluetooth: SCO (Voice Link) ver 0.6
[ 27.788196] Bluetooth: SCO socket layer initialized
[ 27.807803] Bluetooth: RFCOMM socket layer initialized
[ 27.810179] Bluetooth: RFCOMM TTY layer initialized
[ 27.810191] Bluetooth: RFCOMM ver 1.10

 hcitool dev
Devices:
```

While searching the miraculous interwebs, I found out that my bluetooth device should work "out of the box" and I also noticed some other people with different computers and the same computer with the same/similar problems here: [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982")

Any suggestions and help would be greatly appreciated (duh!)

Thanks you guys


**Edit:**
After looking up my computer with my Product Number instead of it's Product Title, HP told me I have a [DV9335NR]("http://h10025.www1.hp.com/ewfrf/wc/product?product=3376902&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us") (Huh? Then why does it say it's a DV9000?)

---

