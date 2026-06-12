---
title: "grub in MBR - or is it?"
date: 2007-04-24
forum: Gentoo and derivatives
---

### Post by tchoklat on 2007-04-24
I have installed SL3.3 and all is fine except I am unable to boot other distros through the SL Grub. How do I know that Grub is in the MBR as it should be (as I am told)? How can I move it there or install it there?

---

### Post by mips on 2007-04-24
In Sabayon you have to edit /boot/grub/menu.lst and add your other OSs there.

---

### Post by tchoklat on 2007-04-24
thanks, i have done that and tried chainloading, copying the actual commands from the menu.lst of the other distros, and configfile. None of them seem to work. I was curious as to whether I installed SL grub in the right place (MBR) and how I check

---

### Post by mips on 2007-04-25
Well if you installed it to the root of the hd then it is in the right place. If you want to reinstall grub simply boot up the sabyon cd again, run the installer, select repair, and select the very last option which only installs grub.

---

