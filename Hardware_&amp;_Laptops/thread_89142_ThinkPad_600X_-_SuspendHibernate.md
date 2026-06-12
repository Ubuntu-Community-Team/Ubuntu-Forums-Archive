---
title: "ThinkPad 600X - Suspend/Hibernate?"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-11-11
Breezy works like a charm on a ThinkPad 600X, but so far I've only been able to get hibernation to work - suspend doesn't work because the machine won't wake up.

I've figured out that these kernel parameters help:

irqpoll (this is enough to get to the Gnome desktop)

acpi=force pci=noacpi (this gets hibernation working)

I've modified /etc/default/acpi-support to uncomment the line that turns on suspend-to-RAM. But I still haven't found the magic kernel parameter that makes suspend-to-RAM work correctly. Does anyone know what it might be?

---

### Post by gmc on 2005-11-12
Umm... I believe that should be "acpi=nopci" not "pci=noacpi".

G.

---

### Post by emendelson on 2005-11-12
That's what I get for writing from memory when the machine is somewhere else. Yes, "acpi=nopci" is what I was using. So the problem with suspend-to-RAM is exactly as it was, unfortunately.

---

### Post by gmc on 2005-11-12
[QUOTE=emendelson]That's what I get for writing from memory when the machine is somewhere else. Yes, "acpi=nopci" is what I was using. So the problem with suspend-to-RAM is exactly as it was, unfortunately.[/QUOTE]

Hmm, ok guess that shoots down that idea then, I was thinking that maybe since the option wasn't activated, that's why it wasn't working. You're not loading any drivers from the restricted modules?

G.

---

### Post by emendelson on 2005-11-12
OK - solved it, with the help of my research assistant, Mr Google:

acpi=off acpi=nopci apm=on

This lets both suspend (via Fn-F4) and hibernate (via the Logout menu) work correctly. I took out irqpoll as these three produced the desired results. Presumably acpi=off and apm=on should be enough, with no need for acpi=nopci, but I haven't tried that.

---

### Post by borris.morris on 2006-10-27
which line do i add it to? i've tried boot, all of them, but it doesn't work

---

### Post by emendelson on 2006-10-28
These are "kernel parameters". You add them at the end of the line that begins "kernel".

---

### Post by borris.morris on 2006-11-02
So, what does your etc/defaults/acpi-support file and kernel line look like? also where do i make perminate changes to grub?

---

### Post by emendelson on 2006-11-02
I no longer use Ubuntu, so I won't try to answer from memory. But you can find dozens of explanations. Just search for "grub" and "menu.lst" and you'll find everything you need.

---

