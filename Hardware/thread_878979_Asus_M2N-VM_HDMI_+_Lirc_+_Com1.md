---
title: "Asus M2N-VM HDMI + Lirc + Com1"
date: 2008-08-03
forum: Hardware
---

### Post by vies on 2008-08-03
Hi everyone,

I have Asus M2N-VM HDMI motherboard that has no Com port in back-IO, but it has Com header on board.

Now for some reason, I can't get lirc to recognize that port. I have serial IR device (irman) that worked great on my previous motherboard.
I have the serialport enabled from bios (3F8/IRQ4).

When I try to start lirc (manually for testing) using following command

sudo lircd --driver=irman --device=/dev/ttyS0, 

lirc starts, tries to connect /dev/ttyS0 and finally it seems to time out and dies. Also none other /dev/ttySx work any better.
I doesn't make any difference if I use lirc from repostories or if I compile it my self.

Has anyone successfully got com port working in this motherboard, or does anyone have any ideas where to start look for the problem?

Do I need to load some modules to enable com port?

Vies

---

