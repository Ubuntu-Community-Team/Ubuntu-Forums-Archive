---
title: "Fluxbuntu 7.10 RC serial port problems"
date: 2008-07-19
forum: Hardware
---

### Post by cytan on 2008-07-19
Hi,
   I'm wondering if there is a problem with fluxbuntu 7.10 rc and serial ports. I have installed it on my thinkpad 390 and have checked that the serial port /dev/ttyS1 is recognised by fluxbuntu using dmesg. However, when I do a 

     ls > /dev/ttyS1

the command never returns. Another test I did is to connect the thinkpad to another LINUX box via the serial port, fluxbuntu cannot talk to it at all. However, when I boot the thinkpad with PiTUX, minicom talks to the LINUX box fine.

    Has anyone successfully used the serial port with fluxbuntu?

Thanks for any info

cytan

P.S. Pardon me for posting a fluxbuntu question here, for some reason I  cannot get registered on the fluxbuntu.org forums

---

