---
title: "Using LIRC with homebrew IR and USB to Serial Adapter"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by oog on 2006-05-19
I've previously successfully set up a homebrew IR adapter with LIRC, but the new computer that I'm working on does not have a serial port. I bought a USB to Serial adapter and I see that ftdi_ser recognizes the adapter and creates /dev/ttyUSB0. What I don't know is how to use this device with the homebrew IR adapter. I would normally use the lirc_serial driver, but I can't figure out what port and IRQ to specify. Anyone have any ideas?

Currently, if I run setup.sh in lirc-0.8.0, I can choose that I have a homebrew IR adapter, but regardless of what I try putting in for the port and IRQ, nothing happens when I run irw. Basically, I run ./configure.sh, make and make install; I modprobe mod_serial; then I run lircd with a lircd.conf that I know works with the remote that I'm trying out. irw connects, but it does not register any incoming signals.

---

### Post by xquisito on 2007-03-22
Hi, 

Have you gotten a solution for your problem?
A have the same situation, and I don't known how to setup the lirc_serial over /dev/ttyUS0 (irq an IO ports).

Thnks,

---

### Post by oog on 2007-03-22
No, I ended up buying a streamzap remote and USB IR receiver, which has reasonable support from LIRC.

---

