---
title: "Solved: Slow Fan Speeds, Laptop Overheating, Help Plz"
date: 2014-04-27
forum: Hardware
---

### Post by ludrak on 2014-04-27
Hello, I just installed Ubuntu 14.04 and the fglrx-updates driver. I'm seeing high temps and low fan speeds on my Acer Aspire 3820g. I tried setting acpi_osi=Linux in /etc/default/grub but it didn't help. I'd guess that the fans are both maxing out at half speed for some reason. Anyone seen this before?

After 15 minutes ofL4D2:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +99.0°C  (crit = +103.0°C)
temp2:        +40.0°C  (crit = +92.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +85.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +86.0°C  (high = +95.0°C, crit = +105.0°C)

Specs are a Core i5 520M and a Radeon HD 5650. I have disabled the Intel graphis in the BIOS.

Edit: There are no fan speed controls in the BIOS.

---

### Post by ludrak on 2014-04-27
Thanks for looking. I just needed to hack the BIOS and hexedit the fan speed tables for the CPU and GPU fans. Seems Acer had over 20 fan speeds and Ubuntu only uses 4. (Three and off.) Incase you guys run into such an issue, I used a program called binmay to edit the KBC tables. I used a Windows program called flupdate from Nuvoton Flash Update to flash the binary. Then I just played with the values based upon others suggestions in another forum. I can't remember my source for flupdate but binmay is at [http://freecode.com/projects/binmay](http://freecode.com/projects/binmay)

---

