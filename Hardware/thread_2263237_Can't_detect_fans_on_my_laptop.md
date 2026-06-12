---
title: "Can't detect fans on my laptop"
date: 2015-01-30
forum: Hardware
---

### Post by hugodaniel2 on 2015-01-30
Hi,

I'm using a Dual-boot with Ubuntu 14.04 and Win 8.1, for work and personal use, on my Asus K52Jc Laptop. 
It's a first generation i5 laptop and it's still working well, but somehow I can't make my fans work, I already tried to check the sensors, according to some hints in other threads, but no fans appear. In Windows they seem to be working fine.

Using the command **sudo sensors**

  I can see that there are no fan sensors available.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +108.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +48.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +47.0°C  (high = +95.0°C, crit = +105.0°C)


```

I already done two suggestions... First, I've installed **HardInfo**, but the same happens with it, there are just no sensors for the fans available...

[ATTACH=CONFIG]259607[/ATTACH]

And then I've tried to install the Intel Microcode, although I don't think it worked well (using Synaptic), since the version that it shows to me, apparently isn't the same that I have running.

Using ```
dmesg | grep microcode
``` I got the following output, and I belive it's not the same as Synaptic is showing me.

```

[    0.000000] CPU0 microcode updated early to revision 0x4, date = 2013-06-28
[    0.211345] CPU1 microcode updated early to revision 0x4, date = 2013-06-28
[    1.099089] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x4
[    1.099095] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x4
[    1.099102] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x4
[    1.099108] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x4
[    1.099169] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba


```

[ATTACH=CONFIG]259608[/ATTACH]

What could be happening so that Ubuntu can't find my fans?

---

