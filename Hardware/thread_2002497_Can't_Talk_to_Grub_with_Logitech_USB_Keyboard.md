---
title: "Can't Talk to Grub with Logitech USB Keyboard"
date: 2012-06-12
forum: Hardware
---

### Post by buzzingrobot on 2012-06-12
Grub2 won't respond to my Logitech Illuminated Keyboard.  I see that's a frequent issue with USB keyboards.  The fix seems to be to enable the USB Legacy setting in BIOS. I've done that, to no avail.

I use a PS/2 keyboard for installs, etc.  Right now, I have the 12.10 alpha on another drive, intending to dual boot with 12.04.  To make a selection from the Grub menu, though, I have to keep the PS/2 keyboard in place.  I'd very much rather not.

Is there a way around this conundrum?

---

### Post by ahallubuntu on 2012-06-12
That's kind of an issue with your hardware, it seems.  Grub doesn't have the ability to load a USB driver to my knowledge - so it has to rely on the BIOS treating a USB keyboard like a "legacy" keyboard.  And if the BIOS can't do it properly, not much Grub can do about it.  Not just a Grub issue.  I've seen the same trouble in Windows with some systems trying to use the F8 key before boot - can't do it on some hardware with a USB keyboard.

You could see if there's a newer BIOS available for your motherboard.

---

### Post by buzzingrobot on 2012-06-12
[QUOTE=ahallubuntu;12021791

You could see if there's a newer BIOS available for your motherboard.[/QUOTE]

I'm running the latest BIOS.  I did find an old, long, and virulent thread on a Logitech forum with many posts about this issue from unhappy customers.  Looks like the board doesn't get enough sustained current to generate keystrokes until after the BIOS and Grub load.  I pulled out a powered USB hub and gave that a try.  Nada.   Using a USB-PS/2 converter produced an unilluminated and unresponsive keyboard.

My mouse works fine in the BIOS.  Too bad Grub can't use it.

I wonder if there's a niche market for a PS/2 gadget to handle this problem. Just a couple buttons that can be set to emulate delete, shift, esc, etc.

---

