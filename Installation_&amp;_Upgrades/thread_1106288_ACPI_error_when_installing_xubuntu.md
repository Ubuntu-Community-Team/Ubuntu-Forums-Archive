---
title: "ACPI error when installing xubuntu"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by marlongpa on 2009-03-25
I am trying to boot Xubuntu 8.04 (on cdrom) for the first time on a Gateway PC with 12.75GB hard drive space and 190mb RAM. It did have  Windows XP on it but that partition was deleted.

However, when I try to run or install Xubuntu, I get an error that's something like "ACPI: BIOS age (1999) fails cut off (something), acpi=force is required to enable ACPI.."

What should I do?

Thanks in advance,

- Marlon

---

### Post by Partyboi2 on 2009-03-26
Try adding acpi=force as a boot option. When you are at the main menu of the Xubuntu cd press F6 and add to the end of the line
```
acpi=force
```
then press enter.

---

### Post by marlongpa on 2009-03-26
Tried it, got the same error. :-/

---

### Post by Partyboi2 on 2009-03-26
You could try updating your bios if you are able to.

---

### Post by marlongpa on 2009-03-26
How?

---

### Post by marlongpa on 2009-03-29
bump

---

