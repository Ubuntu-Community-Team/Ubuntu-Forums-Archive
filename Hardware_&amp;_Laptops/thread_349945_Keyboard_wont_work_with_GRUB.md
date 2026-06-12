---
title: "Keyboard wont work with GRUB"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by w0lf19 on 2007-01-30
I installed Ubuntu as a dual-boot with windows XP, and when the PC boots, I cannot select an OS in GRUB (theyre all listed there, but I cannot select between them with my USB keyboard). What can I do to fix this? I really need to get into my XP partition tonight to finish some work.

thanks

-w0lf
Edit/Delete Message

---

### Post by K.Mandla on 2007-01-30
Check the BIOS settings on your computer and see if there's an option to enable USB keyboards at boot.

The problem is (probably) that your computer is expecting to get keyboard input through the PS/2 port, and your USB keyboard isn't monitored until the system loads and it starts looking for the devices.

I almost forgot: It's possible that I'm wrong. ;)

---

### Post by metalf8801 on 2007-12-21
I was having the same problem until I used a usb to ps2 adapter then it work

---

