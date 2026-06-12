---
title: "How can we achive USB 3.0 packet deferring in Linux?"
date: 2019-04-18
forum: Hardware
---

### Post by chavda2 on 2019-04-18
I have questions regarding my custom USB driver and device power state.
Device have one Interrupt endpoint and at the time when driver install it will submit URB and at the time of interrupt IN packet reception driver will again reuse that URB and submit again for next interrupt IN reception.

Now device is go into power down state called U2 when there are no bus activity then at the time when device wants to send data to host using Interrupt IN transfer than host will not able to receive IN packets. I know in USB 3.0 there are no such contentious polling like USB 2.0 instead async notifcation is available over here. So ERDY and NRDY packets manages this interrupt transfer. 

Unfortunately, device is not sending ERDY to hub and host will have no sense further and wait for interrupt IN data forever.

After reading USB 3.0 spec, I came across the new concept called packet deferring,
Section C.1.2.2 in USB 3.0 spec. How could I achieve packet deferring in Linux host side and how I can prevent usb bus link in U0 state keep alive


[ATTACH=CONFIG]283046[/ATTACH]

---

