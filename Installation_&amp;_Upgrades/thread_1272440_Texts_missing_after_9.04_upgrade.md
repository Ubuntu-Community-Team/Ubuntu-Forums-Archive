---
title: "Texts missing after 9.04 upgrade"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by zwanzig on 2009-09-22
After my update from 8.10 to 9.04 all text strings in applications (in web sites, dialogs, menus etc.) are missing until I hold the mouse over them. Also tty2 to tty6 are weird looking graphics instead of login prompts to shell. What can be wrong?
Thank you

---

### Post by dstew on 2009-09-22
This is most likely a problem with the kernel module that is running your display. What is your hardware (computer, display adapter)?

---

### Post by zwanzig on 2009-09-22
Geforce 5700 running the proprietary nvidia driver, on a MSI K8TN FISR motherboard.

---

### Post by dstew on 2009-09-22
What is your display?

---

### Post by zwanzig on 2009-09-22
TFT, connected with VGA.

---

### Post by dstew on 2009-09-22
Boot in Recovery Mode. Try xfix. If that doesn't help, can you at least get a command-line interface? Or, do you get distorted text even with a Recovery Mode boot?

---

### Post by zwanzig on 2009-09-25
xfix made x look unrecognizeble in black and green as if it where out of sync. I have a working commandline at tty1. I've tried restoring old xorg-confs that I know was working before, but they don't do any longer.

---

### Post by zwanzig on 2009-09-29
I get the same screwed up login splash that hangs when I try to load the 9.04 or 9.10 live-cd. Older live-cd:s (7.04) work fine. Is there a module I need to downgrade or what?

---

### Post by dstew on 2009-09-29
You can try to force a VESA driver to start a graphical desktop. I think it is  F6 at the Live CD opening menu that lets you edit the command line. Or, there might be a safe-graphics mode that does the same thing.

If you edit the kernel command line, add **vesa=force** to the end of the line, then try to boot. This might also work on the kernel line in the menu.lst file of an installed system.

---

### Post by zwanzig on 2009-09-30
I "solved" it by downgrading xserver-xorg to 8.10 intrepid version.

---

