---
title: "Laptop USB problem after ACPI=Force"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by DavidRaid on 2008-01-30
Heys, I'm using a Packard Bell Easynote R1 Series laptop. It's a good laptop thats served me well, and has always been relatively Linux friendly with two annoying little problems. One, the battery monitors never showed any information for me, and two, like many PB users, a lack of wifi. 

I eventually solved these problems by adding 'pnpbios=off' and 'acpi=force' to my bootup. Voila, I had wifi and it told me my battery status. I can finally say goodbye to Windows forever. Or so I thought. For some reason, not sure what, nothing USB works anymore on my laptop. No USB mouse, no USB flashdrives. Nothing. This is a real problem for me.

Can anyone help an XP sick Linux fan? I'll appreciate any advice anyone can give, I'll type in any Terminal commands to get any information you'd like to help and etc, etc. Please, help me. :(

---

### Post by Navaja on 2008-02-11
Exactly the same problem in Packard Bell R1 easynote using the acpi=force option at boot. If I also set noapic option at boot time the wireless stops working, but the usb ports works fine. Also the cpu frequency scaling doesn't work either. I've tried to find a solution everywhere, but nothing works. I'am attaching all the information that I think could be relevant. 

Please someone that knows of this stuff..., we need some enlightenment.

Cheers.

---

### Post by Navaja on 2008-02-11
Adding the option irqpoll to the kernel at boot time, solved the usb problem for me. Usb and wireless working simoultaneously. :)

Though, the processor frequency scaling still does not works. Does it works for you?.

Cheers.

---

### Post by Navaja on 2008-02-11
After using the computer a while, I notice that with the irqpoll option the computer turns much slower. The hd access are about half as fast. Also, the system became unstable, and often completely hanged. Still looking for a solution. The problem clearly has to do with IRQ ports, but I don't know enough yet to fix it.

---

### Post by DavidRaid on 2008-06-08
Thanks for the advice, I've been offline for almost 6 months now after the motherboard on the laptop gave out, whenever I've had access to a machine I've used it only for work. Its only now that my laptop is repaired that I've thought to check for replies, I can't wait to try your suggestions. Thanks! :)

There isn't a way to get Beryl working on this machine is there? I've had no luck.

---

