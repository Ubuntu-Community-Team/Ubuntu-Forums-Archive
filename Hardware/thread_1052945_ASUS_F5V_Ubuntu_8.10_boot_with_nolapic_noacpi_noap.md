---
title: "ASUS F5V Ubuntu 8.10 boot with nolapic noacpi noapic"
date: 2009-01-28
forum: Hardware
---

### Post by polig4e on 2009-01-28
Hello,

I am having trouble booting ASUS F5V with Ubuntu 8.10 on battery. If I use the options "noapic noacpi nolapic" together, it boots, but I only see one core. (Intel Core Duo CPU)

I read that "The problem with using "noapic" is it makes it impossible for the two cores to communicate, since the APIC sends interrupts between the two cores. So you only get one of your two cores in that mode."

However the laptop freezes otherwise when switched to battery power. Even when using AC, it freezes after a few hours of work. Any ideas what I need to do to make it work on battery, not freeze, and see both cores?

Thank you!

---

### Post by dazer26 on 2009-10-13
Hey i'm having the same problem.  When i try and boot on battery power it freezes about 20% in.  When i'm booted up and remove the power cord it also freezes.  I put acpi=off in the boot options, which fixes teh freezing, but now I can't see how much battery life I have left (or how hot my cpu is).  i found an old forum post with the same problem [http://ubuntuforums.org/showthread.php?t=599810](http://ubuntuforums.org/showthread.php?t=599810).  So this has been a problem for a while now.  In that forum it said to use nosmp and noapic instead of acpi=off, but it still freezes when booting on battery.  Considering that forum post is a few years old it doesn't seem like anyone has found a fix for this yet and likely 9.10 will still have the glitch.  Any ideas?

In the other forum most of the people had asus motherboards, i'm using an older compaq (HP) presario 2100 laptop tho.

---

