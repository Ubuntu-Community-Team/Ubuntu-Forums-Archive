---
title: "Problems with serial port"
date: 2008-07-22
forum: General Help
---

### Post by cytan on 2008-07-22
Hi,

First, apologies for posting this in the ubuntu forum. I am having problems getting registered on the fluxbuntu forums and hopefully people can help me here.

I'm wondering if there is a problem with fluxbuntu 7.10 rc and serial ports. I have installed it on my thinkpad 390 and have checked that the serial port /dev/ttyS1 is recognised by fluxbuntu using dmesg. However, when I do a

ls > /dev/ttyS1

the command never returns. Another test I did is to connect the thinkpad to another LINUX box via a null modem cable, fluxbuntu cannot talk to it at all. However, when I boot the thinkpad with PiTUX, minicom talks to the LINUX box fine and ls > /dev/ttyS1 works fine.

Has anyone successfully used the serial port with fluxbuntu?

Thanks for any info

cytan

---

