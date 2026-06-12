---
title: "Accessing Palm via serial"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by steevc on 2006-04-01
I've had my USB Palm (Zire 71) working, but now I want to sync an old IIIx with a different account. I only have a serial connection for it. My PC only has one serial port (Asus A7N266VM motherboard). I've set up kpilot to use /dev/ttyS0, but can't get anything to happen. I've tried all sorts of variations including ttys0, ttyS1 etc with no result. I had to add the user to the tty and dialup groups to give them access to those devices.

Should it not be more obvious what device corresponds with a particular port? It's not very user friendly for the beginner. Tell me if I'm missing a more obvious solution.

---

### Post by biodiesel-bri on 2006-04-01
The pilot-link tools will make it much easier to get up to speed.  I don't recall the exact process but pilot-link.org should be your friend.  I had to set up serial access ages ago and it involved changing permissions and issuing some commands via mknode.

---

