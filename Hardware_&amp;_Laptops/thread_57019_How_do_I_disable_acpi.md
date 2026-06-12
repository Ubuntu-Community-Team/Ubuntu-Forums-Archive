---
title: "How do I disable acpi?"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by numberexhaust on 2005-08-14
How do I disable acpi?  I have a wireless card that's being detected by my system, but it doesn't seem like the card is being powered, so this is my next troubleshooting step (compliments of azz).

Thx

---

### Post by nad on 2005-08-15
At the grub menu selection screen, highlight the kernel command line and press "e" to edit that line. Add acpi=off to the end of the line, press enter then b to boot your computer.

The change you have just made is for this session only. To make it permanent (if it solves your issue), edit /boot/grub/menu.lst to include this option.

You may wish to peruse [http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO)
for a complete description of available boot arguments.

---

### Post by dethredic on 2008-06-29
Sorry, but I need to try disabling this in Hardy. Which line to I add it to?

---

### Post by ibutho on 2008-06-29
Edit the grub entry for the kernel that you use and add "apci=off"  (minus the quotes) to the end of the line that starts with the word "kernel".

---

### Post by dethredic on 2008-06-29
thanks thats what I needed.

---

