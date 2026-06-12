---
title: "Fan not throtling on thinkpad e520 when discrete (radeon) graphics is off"
date: 2011-12-27
forum: Hardware
---

### Post by bss on 2011-12-27
Hello guys!

I have a strange issue. I have just bought a new Lenovo thinkpad edge e520 and installed ubuntu on it. It has switchable (hybrid) graphics so I am able to turn off the Discrete (Radeon) graphics in order to save power. But when I do (i did it on boot in /etc/rc.local: echo "OFF" >  /sys/kernel/debug/vgaswitcheroo/switch) the fan speed does not resspond to any load. That is the laptop gets really hot (cpu temp about 75-80 C), when discrete graphics is turned off at boot.

However, if I turn the discrete graphics card on, the fan starts working (throtles nicely and cools down the laptop.). If I turn the discrete graphics off again then the fan stays at the same speed as it was when the graphics card was turned off. 

Sensors output:
```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +20.0°C  (crit = +120.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:       -128.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +78.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +79.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +78.0°C  (high = +86.0°C, crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM


```

I have also noticed that 
```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +20.0°C  (crit = +120.0°C)

``` is not changing if the discrete graphics is off.

If I run windows, then the fan works OK.

I'm running Ubuntu 11.10 amd64 - Linux 3.0.0-14-generic

---

### Post by bss on 2011-12-29
*bump*

I have also found a thread on Lenovo Community Forums about this problem:

[http://forums.lenovo.com/t5/ThinkPad-Edge/E520-Fan-sometimes-not-working-after-switchable-graphic-issue/td-p/586829](http://forums.lenovo.com/t5/ThinkPad-Edge/E520-Fan-sometimes-not-working-after-switchable-graphic-issue/td-p/586829)

I'm still trying to figure it out weather the problem lies in drivers or bios or the hardware implementation itself.

Regards!

---

### Post by jandd on 2012-01-25
> **bss said:**
> *bump*

I have also found a thread on Lenovo Community Forums about this problem:

[http://forums.lenovo.com/t5/ThinkPad-Edge/E520-Fan-sometimes-not-working-after-switchable-graphic-issue/td-p/586829](http://forums.lenovo.com/t5/ThinkPad-Edge/E520-Fan-sometimes-not-working-after-switchable-graphic-issue/td-p/586829)

I'm still trying to figure it out weather the problem lies in drivers or bios or the hardware implementation itself.

Regards!

The Lenovo Forum thread talks about the same issue on Windows systems. I have a Thinkpad Edge E520 1143-3NG using Debian Wheezy (with kernel 3.2.0) and have the same problem with the latest BIOS 1.22 too. I think this indicates a hardware/BIOS problem. Maybe turning the discrete graphics off also turns of the thermal sensor triggering the fan.

I turn on the discrete GPU using vga_switcheroo when I do some CPU intensive work until there is some better workaround available.

---

### Post by Davserer on 2012-04-16
Any news on this? Problem still present at my e420 witch ati+intel graphics...fans start working only after i switch the radeon card back on

---

