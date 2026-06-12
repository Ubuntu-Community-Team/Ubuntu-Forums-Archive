---
title: "Display is only in the center of the screen"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by migedith on 2008-01-18
I have an old NEC Versa SX Laptop and when I run Ubuntu on the Live Cd or off my hard drive the display is centered on the screen.

In the BIOS under "Advanced CMOS Setup" I have tried both on and off under the "LCD Panel  View Expansion" option, and it doesn't fix it.

I have messed around in the screen and graphics setup in ubuntu, but that doesn't work either.

Does anyone know how to fix this problem?

---

### Post by pytheas22 on 2008-01-18
do you know what your video card is?  If not, post the output of

```
lspci
```

also it wouldn't hurt to post your xorg.conf file, which you can view by typing

```
gedit /etc/X11/xorg.conf
```

---

### Post by clsgis on 2008-01-18
I had the same problem with a Compaq Armada 3500.  try turning off the "framebuffer" interface at boot time.  That is, add "nofb" to the kernel command line arguments in /boot/grub/menu.lst.

(I sure would like to see a complete list of Ubuntu's boot options.  Like Knoppix' cheatcodes.txt.  I'll bet there are a lot more controls than the ones shown in the F3-F5 help.  For example what's Ubuntu's equivalent of hsync=68 for monitors that don't detect right?)

If that doesn't work, try booting Knoppix 5.1.1 on the machine.  If it does better, copy the /etc/X11/xorg.conf file Knoppix generated over the one Ubuntu generated.  Sometimes Knoppix does a better job of recognizing old hardware.

---

