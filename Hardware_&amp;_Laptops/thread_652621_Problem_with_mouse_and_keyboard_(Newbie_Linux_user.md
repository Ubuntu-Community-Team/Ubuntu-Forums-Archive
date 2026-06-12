---
title: "Problem with mouse and keyboard (Newbie Linux user here)"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by brady2007us on 2007-12-28
Hi im a new linux user and i searched the forum and couldn't find out a solution to my problem. tho i found many other people having problems just like me. I installed the new linux "gutsy" like 4 hours ago and my keyboard and mouse die randomly in the first 10 minutes after booting up. i tried feisty fawn a few months like 6 or w/e i dont recall but i had the same problem so i went back to windows and now i am sick and tired of windows and want ubuntu but i dont want to not be able to use my mouse and have to go back to windows again yuck if you could help me i would love you forever.
thanks

brady

---

### Post by empthollow on 2007-12-28
i once had a problem where after i installed 3d drivers i would lose my usb mouse on my laptop randomly.  what i found was that it was all usb that i lost. i spent probably about a year searching for a solution but i found one.  you can put this in the menu.lst file right after all the other kernel options
```
noapic irqpoll
```
it was like magic when i discovered it.  i hope it works for you too.

---

### Post by brady2007us on 2007-12-28
to be totaly honest i have no idea where to put that

---

### Post by empthollow on 2007-12-28
ok, i'll do a quick how to.
```
sudo gedit /boot/grub/menu.lst
```
find this section
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8361c515-d381-411a-909c-1a389c7d05cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

at the end of the line starting with kernel put a space after the word "splash" and type
```
noapic irqpoll
```
should look something like this:
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8361c515-d381-411a-909c-1a389c7d05cc ro quiet splas noapic irqpoll
```

hope that's clear

---

### Post by brady2007us on 2007-12-28
thanks im going to go try that right now

---

### Post by brady2007us on 2007-12-28
ok i did it and now im waiting for the mouse and keyboard to stop working if they even do this time
i will let you know if it works

---

### Post by brady2007us on 2007-12-28
nope mouse stopped working still and i know i edited it right

---

### Post by empthollow on 2007-12-29
man that stinks.  does your usb have power after the mouse/keyboard fails.  just wondering if it is usb that fails or if it is a problem with the devices.  if it's usb that might be a little easier to google.  i would probably try googling for more possible kernel options if it's usb because that means that the system is getting confused after most likely a certain device or process is accessed by the system.  this is controled by the kernel and that's what makes me think a kernel option would help.

---

### Post by brady2007us on 2007-12-29
yeah both of them still get power just dosent let me move the mouse or type

---

### Post by brady2007us on 2007-12-29
ive tried unplugging and plugging back in and still no luck

---

### Post by brady2007us on 2007-12-29
could some one add me to aim or msn and help me try to figure out whats wrong?

[email]brady2007us@hotmail.com[/email] <<msn
userblah8  <<aim

---

### Post by brady2007us on 2007-12-29
sorry for multiple posts, my thread is getting buried and i just don't want to have to go back to windows you know? windows blows  and ubuntu looks so nice so yeah I'm still having the problems :(:confused::(:confused:

---

### Post by empthollow on 2007-12-29
i'd like to help you get your periferals working. i'll have some time to google tonite.  I've tried to use windows and i've tried making it look different but the thing i found is that it just doesn't work very good.

try to find some kind of pattern like do you lose your devices after opening a certain application or after a certain amount of time.  also do you have 3d drivers installed and what kind of vid card.  also please post the output of
```
dmesg
```
as soon as you reboot after you lose your devices.:guitar:

---

### Post by empthollow on 2007-12-29
Here are some kernel options.  if you have an older motherboard you may want to try noacpi.  however i think you may want to play around with the irq options.  like acpi_irq_balance.  i would probably try a whole bunch of them at once and see if it helps and then eliminate the ones you don't need once you do get it working

Option: acpi=off OR noacpi

Impact: This parameter disables the whole ACPI system. This may prove very useful, for example, if your computer does not support ACPI or if you think the ACPI implementation might cause some problems (for instance random reboots or system lockups).
Option: acpi=force

Impact: Activates the ACPI system even if your computer BIOS date is older than 2000. This parameter overwrites acpi=off and can also be used with current hardware if the ACPI support is not activated despite apm=off.
Option: pci=noacpi OR acpi=noirq

Impact: These parameters disable the PCI IRQ routing
Option: pci=acpi

Impact: This parameter activates the PCI IRQ routing
Option: acpi_irq_balance

Impact: ACPI is allowed to use PIC interrupts to minimize the common use of IRQs.
Option: acpi_irq_nobalance

Impact: ACPI is not allowed to use PIC interrupts.
Option: acpi=oldboot

Impact: Deactivates the ACPI system almost completely; only the components required for the boot process will be used.
Option: acpi=ht

Impact Deactivates the ACPI system almost completely; only the components required for hyper threading will be used.
Option: noapic

Impact: Disable the "Advanced Programmable Interrupt Controller (APIC)".
Option: nolapic

Impact: Disable the "local APIC".
Option: apm=off OR noapm

Impact: Disable the Advanced Power Management.
Option: irqpoll

Impact: Changes the way the kernel handles interrupt calls (set it to [WWW] polling). Can be useful in case of hardware interrupt issues.

good luck, keep me posted

---

### Post by brady2007us on 2007-12-29
there is no pattern its all random.

---

### Post by empthollow on 2007-12-29
i would play with the kernel options then, you can use "e" durring the grub boot menu to avoid having to edit menu.lst every time.  sounds like the system is not handling the devices properly and it is getting stuck at a device call which are usually determined by irq number. adjusting the kernel options i'm hoping will cause the system to handle the calls differently in a way that isn't problematic. good luck.

---

