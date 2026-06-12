---
title: "Dell Inspiron 8200 not undocking cleanly -- eth1 not cooperating"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by SUparJErk on 2007-11-17
I've got myself a Dell Inspiron 8200 and PRX model docking station, running Ubuntu 7.10. The laptop and docking station work fine together if I boot up with them connected. However, if I dock or undock the computer after it's already powered on, X lags horribly (display and input freeze for a couple seconds every few seconds), the docking station's network controller ceases to function, and I get endless error messages like these spewed to whatever tty I switch to:


eth1: transmit timed out, tx_status ff status ffff
diagnostics: net ffff media ffff dma ffffffff fifo ffff
eth1: Transmitter encountered 16 collisions -- network cable problem?
eth1: Interrupt posted but not delivered -- IRQ blocked by another device?
Flags; bus-master 1, dirty 9096(8) current 9112(8)
[...]
eth1: command 0x5800 did not complete! Status=0xffff


Is this actually a bug or is there some "proper" way to cleanly dock or undock the laptop from within the OS that I'm not aware of?

---

### Post by dralokyn on 2007-11-17
[https://wiki.ubuntu.com/LaptopTestingTeam/Dell](https://wiki.ubuntu.com/LaptopTestingTeam/Dell)
the entry for your laptop doesn't have docking issues tested, but if you know which models are similar, you could look at their pages.

---

