---
title: "USB devices off after waking up from sleep/hibernate"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by MasterOfMuppets on 2007-02-27
I'm in a T42 Thinkpad here and everything's fine, except that any USB devices I have connected to the comp are dead after I wake it up. I have a USB keyboard and a USB mouse, and they just stop responding when I wake up. Re-plugging them doesn't hell either...
I already added the mouse configuration scripts to the resume.d directory, hope that works.

EDIT:
Got some new info. The only thing wrong in the resume process is that the script called 72-acpi-pain.sh can't find a module called apci_sbs .
I will post a full console output the next time I sleep the computer.

---

