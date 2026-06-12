---
title: "&quot;Keyboard failure&quot;"
date: 2008-04-24
forum: Hardware
---

### Post by sexcopter on 2008-04-24
Hi, I have a Dell Optiplex GX260 set up as dual boot (windows and Ubuntu Gutsy, with Ubuntu as default), which has been fine and dandy until now.

I have a Logitech wireless keyboard, and now, when I power up, I get the bios splash screen as usual, then the message "Keyboard failure". Then the grub screen comes up, times out and goes with the default option Ubuntu. Ubuntu boots, and at the log-in screen the keyboard is working fine!

I can't for the life of me figure out what the problem is at boot, which isn't a problem after booting, nor what I can do to diagnose any further. Does anyone have an idea what it could be, or what I can do to find out more? I'm not a complete noob, but I also don't know a great deal.

Thanks,
James.

---

### Post by dmizer on 2008-04-24
is your wireless keyboard connected by usb?  some older bios designs can't recognize a usb keyboard.  so, the bios thinks no keyboard is attached to the machine, and prints a keyboard error message.

you can verify this by simply plugging in a regular ps/2 keyboard for your next boot.  if the message disappears, this is your problem.  you can correct the problem by turning off the keyboard check in the bios.

or, you can just live with it since, as you can see, it really doesn't interfere with the operation of the machine.

---

### Post by sexcopter on 2008-04-25
Good call, when I got home form work I tried putting on a USB -> PS2 adapter and voila, it works when plugged into the old-school keyboard socket.

It doesn't explain why it went wrong, since it was working fine before! Still, I have a working solution, and that's what matters, so thanks a lot!

---

