---
title: "Backlight won't hold setting..."
date: 2008-10-02
forum: Hardware
---

### Post by mikeypizano on 2008-10-02
This is extremely annoying for me. I like to keep my backlight locked to lowest setting, as I did with Vista before I installed Ubuntu. There is a problem where my backlight will go full brightness after a hibernate, or if I open the BasiliskII Macintosh emulator software. 

So the question is: How do I make it keep the backlight at the lowest setting unless I change it, and to go back to lowest setting if I hibernate/suspend/reset/etc.

---

### Post by HarshReality on 2008-10-03
Im Skype you also mentioned your CPU fan issue which according to bug reports seems to be realted to hibernate.. simplest response:

edit /etc/default/acpi-support and commenting out the lines for ACPI_SLEEP and ACPI_HIBERNATE per the instructions.

If the system has issues coming back, just dont send it there ;)

---

### Post by mikeypizano on 2008-10-04
BUMP!

Anyone?

---

