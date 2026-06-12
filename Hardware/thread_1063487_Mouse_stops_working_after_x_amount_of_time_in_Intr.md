---
title: "Mouse stops working after x amount of time in Intrepid"
date: 2009-02-07
forum: Hardware
---

### Post by Shiskimalii on 2009-02-07
I have a Logitech G7 wireless mouse that after a short period of time (log on to half an hour) quits working. I have tried adding the boot option "acpi=force irqpoll" but that didn't fix anything. I have also tried restarting x, by pressing ctrl+alt+backspace, but that just freezes my computer. I have an Asus M3N78 Pro motherboard with the latest BIOS. I have tried lsusb before and after my mouse stops working but nothing changes. I also have a wireless keyboard that will stop working if I have it on usb but my game controller will continue to work. I use my keyboard on ps2 but I cannot use ps2 for my mouse. The mouse also works perfectly in Windows. Please help, Ubuntu is unusable as is.

Solved: Had to disable USB Legacy support in the BIOS.

---

### Post by Asgaroth on 2009-02-21
I kinda have the same problem, but I cant imagine how would that work for you. If I disable legacy support it wont even detect my usb devices in the first place because the usb bus is disabled.
You dont have usb bus? That might explain things.

---

### Post by lastrider on 2009-03-18
I have the same problem, but I fear if I disable USB Legacy support on my BIOS then on grub boot options I won't be able to choose which OS to boot into since both my Keyboard and Mouse is Wireless via USB. #-o

Any recommendations?

I'm using both 8.10 and 8.04 and it occurs in both versions... 8.04.1 kernel 2.6.24-19-generic. I installed 8.10 on another partition just to test whether the mouse problem was fixed but it doesn't seem so.

---

