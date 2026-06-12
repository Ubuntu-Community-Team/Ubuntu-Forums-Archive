---
title: "Internal card reader not responding"
date: 2020-09-15
forum: Hardware
---

### Post by Enigma12 on 2020-09-15
I recently installed, as in physically mounted, a multi-card (CF ++++ reader) into one of my desktop computers. It is not working. I plugged its data cord into a USB socket on the motherboard in a way that mated plug and socket, but without any instructions. Later I found a video that said to plug it in with the red wire, which mine has, to the left, but neither the card reader in that video nor the computer matched mine. So, I plugged mine that way. It is still not working. 

I ran lsusb in terminal and got the below results: 

```
wayne &#57520; ~ &#57520; lsusb
Bus 002 Device 004: ID 045e:0780 Microsoft Corp. Comfort Curve Keyboard 3000
Bus 002 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The card reader doesn't seem to show up in that list, nor does it show in either Disks or File Manager. Have I killed that card reader by incorrectly pluggng it in, or is there some command that I need to run to activate it?

---

