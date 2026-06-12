---
title: "ACPI scripts: Can't find any /var/lib/acpi-support/lidstate"
date: 2008-09-17
forum: Hardware
---

### Post by bogoliubov on 2008-09-17
Hello. I'm investigating why my laptop can suspend from the menu, but not by closing the lid. 
Anyway, I looked in the /etc/acpi/lid.sh script, and inside there's a script that is called in the beginning: /usr/share/acpi-support/power-funcs

In this script, a variable called LIDSTATE is set to '/var/lib/acpi-support/lidstate'.
However, I can't find this file! Shouldn't I have one and, if so, can this be an explanation for my lid suspend problems!?

---

### Post by bogoliubov on 2008-10-09
bump...?

---

### Post by rabbitear on 2009-06-02
I'm having the same exact issue.  Jaunty on an HP Mini 2140

no /var/lib/acpi-support/lidstate

---

