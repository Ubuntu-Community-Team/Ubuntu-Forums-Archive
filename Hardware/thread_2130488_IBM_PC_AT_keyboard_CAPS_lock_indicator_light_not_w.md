---
title: "IBM PC AT keyboard CAPS lock indicator light not working"
date: 2013-03-29
forum: Hardware
---

### Post by notmistaken on 2013-03-29
My classic IBM PC AT 101 key keyboard (Model no. 1398609, manufactured in 1992) works in every aspect except that the LED indicator light for the CAPS lock key does not light upon key press, yet the CAPS lock itself works. The other LED indicators for NumLock and ScrollLock work fine.

This CAPS lock LED indicator light works fine on a Windows 7 machine and works fine in the BIOS and Ubuntu GRUB. I am using Ubuntu Server, 10.04.4 LTS.

Interestingly, when I execute the command:
setled -L +caps
the LED works.

I have tried to reconfigure the console setup with the command:
dpkg-reconfigure console-setup
and selected a Generic 101-key PC keyboard and rebooted and this made no difference.

Please note that this is a Server installation, so does not have X installed, so no X-specific solutions are applicable.

Although this is a minor issue and I can live with it, I'm still curious as to why this is happening and at a loss to explain why this is the only problem I can find with using this ancient keyboard with Ubuntu Server.

---

### Post by tgalati4 on 2013-03-29
Have you tested it in Windows 3.1 to see if it lights up?

You could load the xorg libraries but not run the server and see if that helps.  Try loading a LiveCD of an older Ubuntu distro or the Desktop 10.04 and see if it works.  That might narrow down the issue.

Perhaps the Capslock key definition was modified.

What is the output of:  (In a real console, Control-Alt-F3)

```
dumpkeys -i > dumpkeys.txt
cat dumpkeys.txt
```

On a Linux Mint 14 Mate (based on 12.10)

tgalati4@Mint14-Extensa ~ $ cat dumpkeys.txt 
keycode range supported by kernel:           1 - 255
max number of actions bindable to a key:         256
number of keymaps in actual use:                 128
of which 121 dynamically allocated
ranges of action codes supported by kernel:
number of function keys supported by kernel: 256
max nr of compose definitions: 256
nr of compose definitions in actual use: 68

Between* loadkeys* and *dumpkeys* you may be able to find the difference.

Have you tried the Generic 102, 104 or 105 keyboard definitions?

---

