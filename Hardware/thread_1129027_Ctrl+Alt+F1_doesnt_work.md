---
title: "Ctrl+Alt+F1 doesnt work"
date: 2009-04-18
forum: Hardware
---

### Post by falstaff on 2009-04-18
Hello,

On my Laptop HP EliteBook 8530w with Quadro FX 770M graficcard the virtual consoles on F1-F6 doesnt work... I used to have this with Intrepid and now with Jaunty too... Sometimes the system get back to X by itself (usually the first time i press Ctrl+Alt+F#), sometimes i have to switch back to X by myself. But there is never a virtual console displayed! It seems no like a real black, more like a "screen is out" black... Any idea?

Ah yes, i use nvidia binary drivers...

Thanks
falstaff

---

### Post by ajmorris on 2009-04-19
hi there,
are you running boot framebuffers at all? Also, can you please post the contents of your /boot/grub/menu.lst

This sort of behaviour, is quite common if you're using framebuffers, but the color depth specified is out of range, or a kernel module is not compiled to support the framebuffers you are trying to use etc etc.


AJ

---

