---
title: "Pointer freezing on 13.10 (64 bit), HP Pavilion Sleekbook 15."
date: 2014-01-07
forum: Hardware
---

### Post by Marzian on 2014-01-07
Hello,
I've had the problem in the title for months, but I can't find a pattern for the reason: the pointer of the touchpad keeps freezing out of the blue...

Sometimes I can solve using "sudo modprobe -r psmouse" and then "sudo modprobe psmouse", but even in this case I don't see a pattern for the times when it works and those when it doesn't. 

In the latter case, I have to reboot (with Unity) or even shutdown (with KDE).

Where can I start to look?

Thanks!

---

### Post by Marzian on 2014-01-08
Any ideas? Even a workaround command different from modprobe would be fine!

---

### Post by Marzian on 2014-02-16
Some more information:

- If I wait long enough, sometimes the pointer starts working again

- Another problem is when - out of the blue - a certain key that I have just pressed starts to auto-digit itself, (for example: thisssssssssssssssssssssssssssssssssssss)

Any idea?

lsusb, if it can be useful:

Bus 002 Device 003: ID 05c8:0355 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:1000 Ralink Technology, Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Marzian on 2014-07-02
Late update:

Finally solved after the upgrade to the latest Ubuntu edition!

---

