---
title: "Ubuntu shutting laptop down at 70C"
date: 2014-05-29
forum: Hardware
---

### Post by mike198 on 2014-05-29
Hi, 

This is a new install of Ubuntu on my laptop. 

Ubuntu has been shutting down with a thermal error even when the laptop is obviously cool. It seems to be shutting it down at about 70C. 

I do have lm-sensors installed and when I type ´sensors´ at the prompt it returns with...
[SIZE=1]Adapter: Virtual device[/SIZE]
[SIZE=1]temp1:        +66.0°C  (crit = +102.0°C)[/SIZE]
[SIZE=1]temp2:        +44.0°C  (crit = +92.0°C)[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]coretemp-isa-0000[/SIZE]
[SIZE=1]Adapter: ISA adapter[/SIZE]
[SIZE=1]Core 0:       +67.0°C  (high = +95.0°C, crit = +105.0°C)[/SIZE]
[SIZE=1]Core 2:       +60.0°C  (high = +95.0°C, crit = +105.0°C)[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]radeon-pci-0200[/SIZE]
[SIZE=1]Adapter: PCI adapter[/SIZE]
[SIZE=1]temp1:        +78.0°C  [/SIZE]

Leading me to believe it should go to at least 100C before shutting off. 

I HAVE INSTALLED psensor...which also shows the readings at round 70C...but its alert settings are set lower. I´ve changed those, but CAN psensor TURN YOUR LAPTOP OFF??

This is my work machine (I´m a developer) and I prefer to work in Linux than Windows...but I can have the machine shutting off unexpectedly. 

Thanks!
Mike

---

### Post by tgalati4 on 2014-05-29
Look in your BIOS, that is typcially where hardware temperature monitoring is set.  Normally ACPI interrupts (like thermal shutdown) will happen before the OS has a chance to think about it.  You don't want to run your CPU at 100C that can cause warping and permanent damage to the motherboard.  The CPU can probably take it, but the small motherboard traces can't, and if they get cracked, your machine becomes ewaste.

What model laptop?  You should investigate what is causing the high temperatures.  Normal CPU's will run at 50 to 60C max, 30C at idle.

---

### Post by jeanfi on 2014-05-31
> **mike198 said:**
> 
I HAVE INSTALLED psensor...which also shows the readings at round 70C...but its alert settings are set lower. I´ve changed those, but CAN psensor TURN YOUR LAPTOP OFF??


At least on last releases, by default the alarm threshold of psensor is... 0C. When you enable the alarm for a sensor, you have to define the high and low threshold (that's in the same settings panel).
Psensor CANNOT turn off the computer, that's just a monitoring software.

Take a look to your syslog, it might be the kernel itself which does the shutdown otherwise it is probably the HW/BIOS.

Modern CPUs on desktop can reach 60/70 on heavy load with "normal" cooling but 80/90C can be easily reach on laptops, at least that's my experience with few DELL, Lenovo W510/530, and Macbook pro.

---

