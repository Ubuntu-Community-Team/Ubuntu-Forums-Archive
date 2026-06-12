---
title: "Infrared probably not as hard as I'm making it..."
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by wsmoser2004 on 2007-07-28
I have an HP zt3000 laptop, and I couldn't care less whether the infrared port worked until a few weeks ago, when I got a cell phone with an infrared port.  Now I'd like to get it working, but I can't figure out how.  I've read a few different howtos and tried lots of things, but nothing has worked.  I think it's probably something really simple that I haven't done yet.  

Here's what I know:

- Windows detects it as an SMC-IrCC chip (and it works under Windows)
- It supposedly supports FIR (Fast Infrared)
- I have loaded lots of kernel modules, including ircomm_tty, irtty_sir, smsc_ircc2, irda
- I have irda-utils installed
- I've run through 'dpkg-reconfigure irda-utils' a few times...I picked "native" chip, and then "smc-ircc" as the type
- 'irdadump' never produces anything for me, and when I Ctrl-C it, it says "0 packets received by filter"
- My phone tells me it doesn't detect any devices when I try to search for the laptop
- 'findchip -v' does not seem to find anything

Is there any way to determine if Ubuntu can actually "see" the infrared device?  For example, I've tried 'lspci' and 'lshw,' and neither of those seem to indicate that I even have an infrared device, although maybe it's just obscurely-named.

I'd appreciate any ideas/suggestions :).

---

### Post by Offoffoff on 2007-08-05
Hello! Have the same problem. In my HP Compaq nc4000 I have IrDA controller, but cannot get it working. I am suspecting this is the same SMC-IrCC-chip, but maybe not, because have an ALi chipset inside of notebook.

---

### Post by shadwstalkr on 2007-08-16
I also have an HP Pavilion zt3000 laptop with Feisty, and I figured out how to get the IrDA working.  

Make sure you have the package irda-utils installed.

Put the following two lines at the bottom of /etc/modprobe.d/irda-utils
```

options smsc-ircc2 ircc_irq=4
alias irda0 smsc-ircc2

```

Get it started by running
```

sudo /etc/init.d/irda-utils restart

```
and you'll have a network interface called irda0 and a serial device at /dev/ircomm0.

Now the infrared port will work, but it has to be reset every time you suspend and resume the laptop.  To fix this, go into /etc/default/acpi-support and change the line
```

RESTART_IRDA=false

```
to
```

RESTART_IRDA=true

```

I've only tried this on my laptop, but it might work for other systems.  The problem seemed to be that the SMSC driver was choosing an interrupt that conflicted with my parallel port.  I just forced it to use one that wasn't being used (look in /proc/interrupts).

---

### Post by tgalati4 on 2007-08-17
Make sure your phone is within 2" to 4" of the infrared port.  You would think you could transmit across the room (like a TV remote) but the protocol only works at close distance.

Oh, and it's slow as dirt.  Fast IR means slightly faster than slow as dirt.

---

