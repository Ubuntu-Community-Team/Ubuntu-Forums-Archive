---
title: "Swissonic easy usb - external sound card"
date: 2012-12-09
forum: Hardware
---

### Post by jck32 on 2012-12-09
Hi,

i'm trying to get my external sound card to work with linux.
It is called Swissonic easy usb.

Output of lsusb:
```

...
Bus 004 Device 003: ID 152d:2539 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 003 Device 003: ID 170b:0020 Swissonic 
```So it is there.

When i try to find a driver with `hwinfo --sound`, the external sound card is not displayed, just the onboard one.

I tried out all 'usb' drivers with 'snd' but the device is still not in 'proc/asound/cards'.


Maybe someone knows a driver i could try.

I also tried to find one on the internet, but there seems to be nothing there.

---

