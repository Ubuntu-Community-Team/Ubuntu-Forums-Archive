---
title: "Ubuntu boot problems (perhaps ACPI)"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by pteron.dk on 2007-05-22
Hello wise Linux guys!

I've bin flirting with Linux for some years now (Debian), and this week I decided to take step and commit myself to Ubuntu completely. (Almost) everything worked great, and I wanted to install Ubuntu on my laptop too. 
When I booted my laptop with the Ubuntu CD in it and pressed "Start or install Linux" it just halted after the "Loading Linux kernel..." with the black screen and the white underscore blinking. 
Then I thought it might have something to do with the ACPI, and then I tried booting with "acpi=off" which worked fine and I installed Ubuntu without problems.
Then I had to reboot and then the computer just halts with "Starting up...", and when I try to boot with "acpi=off" the laptop restarts immediately.

I hope there is a way to get it to work because Ubuntu is sooo nice!

Linux: Ubuntu 7.04 (32bit) (kernel 2.6.20-15)
[Laptop specs. (M2400N)]("http://www.asus.com/products4.aspx?modelmenu=2&model=34&l1=5&l2=26&l3=124&l4=0")

---

### Post by pteron.dk on 2007-05-29
Anyone?

---

### Post by maksei on 2007-05-29
have you tried other cheatcodes, like "noacpi noapic nolapic irqpoll pci=routeirq ide=nodma"?

try these separately and in combinations

also, you probably need to add some of these codes to your grub

so try booting, then hitting 'e' to edit the grub boot parameters, then adding cheatcodes to the appropriate line, then pressing enter and 'b' to boot with your parameters

in fact you should be able to copy the boot parameters from your debian install

---

### Post by nutz on 2007-05-29
When you disable the ACPI you are also disabling devices that depend on it. Perhaps one of those devices is the source of the lockup...

---

### Post by pteron.dk on 2007-06-02
I'll try that when I get home. But anyway, this is a bypass. Is the problem known and is there a way to fix it?

---

### Post by pteron.dk on 2007-06-02
Ah, it worked with the work around. Now I'll start getting hardware to work. Thx u guys

---

