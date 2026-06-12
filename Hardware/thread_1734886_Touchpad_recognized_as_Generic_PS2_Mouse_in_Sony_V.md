---
title: "Touchpad recognized as Generic PS/2 Mouse in Sony Vaio VPCEE42FX"
date: 2011-04-20
forum: Hardware
---

### Post by Moulinoski on 2011-04-20
I've searched Google and I've seen threads from this very forum to only find that no solution seems to really work for me. After pretty much three months of guess work, I'm finally asking here...

I'm using a Sony Vaio E-Series VPCEE42FX Laptop. The touchpad WORKS but there is no edge scrolling. Going to Preferences > Mouse, there is no Touchpad option and in Pointing Devices, I only have Generic PS/2 as a mouse. I've tried using the solution for editing grub's GRUB_CMDLINE_LINUX to have "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" (and I once even tried amd64.nopnp, since I'm using 64-bit Ubuntu) in vain.

Is there any fix for this problem? If I need to clarify, please say so.

---

### Post by oddchild on 2011-09-24
i have the same issue. it is quite annoying, as while typing my palms continuously tap and move the cursor to another point...

---

### Post by 0wDJ on 2011-11-08
Got the same problem...

---

### Post by faromount on 2011-11-27
Hey chaps, Ubuntu have a fix.

[https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty#KeyboardTouchpad](https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty#KeyboardTouchpad)

---

