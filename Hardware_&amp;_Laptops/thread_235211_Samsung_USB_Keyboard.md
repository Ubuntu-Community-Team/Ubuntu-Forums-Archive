---
title: "Samsung USB Keyboard"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by flemmingesm on 2006-08-12
I have a Samsung pleomax USB keyboard, that works fine i win XP.
The keyboard works fine in bios and also when I get to the boot options, where I can choose between Win XP and Ubuntu.
But as soon as Ubuntu starts up I have no keyboard.
Does anyone have an idea???

Flemming Mørup
Denmark

---

### Post by flemmingesm on 2006-08-14
New information added:

- In the device manager I can see the entry USB compliant keyboard.
- The keyboard works fine in Feather linux Live CD (Knoppix remaster)
- Even though I can use the keyboard in BIOS, I can't actually enter the
  BIOS by hitting del. I have to hit del on a ps/2 keyboard.

If anyone has an idea, please let me know!

Flemming Mørup
Denmark

---

### Post by maubp on 2006-08-15
Are there any BIOS settings about supporting USB keyboards?

---

### Post by flemmingesm on 2006-08-16
Yes. I have the option to enable or disable legacy USB for mice and keyboards. And I can choose wich USB ports to enable. I have tried all options... 
The motherboard has two USB 1.1 ports and I have a PCI card with two USB 2.0 ports. I assume I should use the 1.1 ports that are on the motherboard, but I have tested the 2.0 ports as well. Nothing seems to work...

Flemming Mørup
Denmark

---

### Post by maubp on 2006-08-16
It probably depends on your machine, but I would guess the legacy USB keyboard/mouse support will only work using the ports on the motherboard itself.

I had a dual boot shuttle.  With a PS/2 keyboard everything was fine.  With a USB keyboard, it worked fine in Ubuntu itself, and in Windows XP.  However...

When the legacy USB support was turned off, when using my USB keyboard I couldn't get into the BIOS (it didn't see the keypress) and I couldn't change the OS at the boot selector.  So I could only boot Ubuntu - which would then recognise the keyboard. 

Once I turned on the legacy support in the BIOS (using a PS/2 keyboard) then I was able to use the USB keyboard in the BIOS and in the boot selector.

It sounds like you have tried all the obvious things.  Can you borrow a different USB keyboard to see if that helps?  Can you use a USB/PS2 adaptor on your keyboard?  I did this on my mouse so as not to "waste" a USB port.

---

### Post by flemmingesm on 2006-08-16
I will try the adaptor solution, but it is not the optimal solution, since the keyboard has a built in 2 port USB hub that I want to use.
I guess it should be possible to connect via USB since it is possible in Feather (Knoppix remaster).
I am very new to Linux, so i don't know anything about kernel or terminal...

Flemming Mørup
Denmark

---

### Post by flemmingesm on 2006-08-17
After an update, it seems that the problem has solved itself, but i have no idea what part of the update it was...

Flemming Mørup
Denmark

---

### Post by maubp on 2006-08-17
An Ubuntu update? - well that's good news :)

The only other thing I could think of was to see if there is an update to your motherboard's BIOS. Personally I don't like updating that sort of thing unless I have too - just in case it goes wrong or makes something worse.

---

### Post by flemmingesm on 2006-08-18
Yes. I just installed every update available in the update manager (180 MB), and then it worked, almost...
The keyboard has to USB ports and I have attached a USB mouse to one of them. This works fine, but if I attach a wireless USB network stick to the other one, the computer crashes. I can live with this, since i can just plug it into another USB port. It just puzzles me...
I'm not to keen on updating BIOS either, if it is not absolutely necessary...

Flemming Mørup
Denmark

---

