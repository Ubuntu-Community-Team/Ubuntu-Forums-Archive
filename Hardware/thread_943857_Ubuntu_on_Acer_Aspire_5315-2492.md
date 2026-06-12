---
title: "Ubuntu on Acer Aspire 5315-2492"
date: 2008-10-10
forum: Hardware
---

### Post by Patrick793 on 2008-10-10
Hi all. I just got a new laptop, and, like my desktop, I want to install Ubuntu on it. I have 2 copies of Ubuntu 8.04 Hardy Heron (not 8.04.1)

EDIT: Sorry, messed up and accidentaly hit post.

Anyway, when I boot from the CD, it freezes right before it hits the end of the bar. (back and forth motion), and when I use the line acpi=off, I get a busy box terminal.

How can I bypass these and install Ubuntu? This very disk worked on my desktop.

---

### Post by phidia on 2008-10-10
You must be using the live cd (desktop version) right?

Anyway you can press the F4 function key and choose "Safe graphics mode" and see if that gets you to the desktop.

---

### Post by Patrick793 on 2008-10-10
I'll try that in about an hour if the new ISO I'm downloading doesn't work.

---

### Post by Patrick793 on 2008-10-10
Safe Graphics Mode doesn't help.

I removed the quiet--splash part of the boot, and this is the last line.

```
[   42:180130] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
```

After that the drive stops reading the CD.

Any help?

---

### Post by Patrick793 on 2008-10-11
I've tried the Alternate Installer.

Same thing...

---

