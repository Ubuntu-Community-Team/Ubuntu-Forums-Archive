---
title: "Grub doesn't respond to USB keyboard"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by montgoss on 2007-06-02
My USB keyboard works fine in the BIOS.  But the second grub starts, the keyboard stops working.  Works just fine again once Ubuntu or Windows is loaded.

Do USB keyboards normally work in grub?  Do I need a different version of grub?  Any ideas?

--edit--
BTW, in my searching I saw several people mention that sometimes the keyboard needs to be plugged into a specific port.  Well, I tried all 6 USB ports.  All 6 work in BIOS but not with GRUB.

---

### Post by Ken_Lewis81 on 2007-06-02
If there is an option for your BIOS to provide 'Legacy USB support' then you'll need to select that; GRUB is expecting to talk to a keyboard via the old PS/2 standard and doesn't know what USB is.

Take care.
Ken.

---

### Post by montgoss on 2007-06-03
That did it.  I dug around in the BIOS found that option.  Now grub responds to my keyboard.

---

### Post by w0utje on 2007-10-24
thnx that helped :D

---

### Post by Tombo5150 on 2008-01-02
Ran into the same problem myself, thank you soo much!

---

