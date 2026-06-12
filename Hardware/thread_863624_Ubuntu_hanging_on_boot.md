---
title: "Ubuntu hanging on boot"
date: 2008-07-18
forum: Hardware
---

### Post by dgiglio84 on 2008-07-18
Hey everyone.  First of all I must say that I've been using Ubuntu for about six months now and I absolutely love it.  However, I'm having a problem when I boot Ubuntu on my Toshiba Satellite laptop (model L25-S119).  On the "Ubuntu" splash screen, the progress bar will freeze for anywhere from 15 seconds to one minute, then continuing booting.  Upon turning off the splash screen, I noticed the system would hang after the following line:

> ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

I also noticed I get this message when I start Ubuntu:

> MP-BIOS bug: 8254 timer not connected to IO-APIC

After doing some research, I was able to get rid of both the MP-BIOS bug and the boot hanging by adding "acpi=off" and "noapic" to the grub boot line.  However, after adding these switches, I wasn't able to see my battery charge.

Is there any way to fix these problems without sacrificing my battery charge meter?

I am using Ubuntu 8.04.1.

---

### Post by dgiglio84 on 2008-07-19
*Bump*

I also tried using irqpoll and updating my BIOS, but it did nothing.

---

### Post by dgiglio84 on 2008-07-22
I figured out a workaround to the problem.  Apparently it had nothing to do with the message I had quoted before, but rather the messages that proceeded it:

> Clocksource tsc unstable (delta = -2090960056 ns)
Time: acpi_pm clocksource has been installed.


Adding "clocksource=acpi_pm" to the boot line in /boot/grub/menu.lst fixes the hang-up, but I'm still getting the "clocksource tsc unstable" message.  Oh well...at least I can boot up in under a minute now. :)

---

### Post by Jackelope on 2008-07-30
Thanks, dgiglio! My computer hung halfway through booting but this fixed it! This fix should be put somewhere permanent because I know quite a few people who had this same problem and this worked great.

---

