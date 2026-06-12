---
title: "HP Z820 USB3 Devices Disconnects after a few minutes"
date: 2019-02-02
forum: Hardware
---

### Post by sheenlim08 on 2019-02-02
I have several external SSD and HDD that is connected via USB3.0, however today the USB3 ports is having problem.

dmesg:
[https://paste.ubuntu.com/p/RckNzg3psd/](https://paste.ubuntu.com/p/RckNzg3psd/)

I can tell that it is not the USB device that is having problem because when I connect them to a USB2 i can see them.

After a minute or two I can see that all USB3 devices are being disconnected. The dmesg information link is above. And when I disconnect the External USB3 HDD & SSD and reconnect them back, the system does not detect them, even the dmesg not not populate when reconnecting them on a USB3 port. Connecting them on a USB2 port have good result.

I even tried to update to the latest Linux Kernel v4.20.6 if that helps,but it didn't.

Any ides?

---

### Post by sheenlim08 on 2019-02-16
Here another dmesg information:
[https://paste.ubuntu.com/p/tSvjBsMdyR/](https://paste.ubuntu.com/p/tSvjBsMdyR/)

I also noticed that it only happens when I transfer USB3-USB3 data. It does not happen when USB2-USB3 or USB3-USB2.

---

