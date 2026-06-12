---
title: "How to write a script that executes when laptop lid is opened?"
date: 2008-10-29
forum: Hardware
---

### Post by fongandrew on 2008-10-29
Hi all,

Currently, my laptop (T400 Lenovo with integrated X4500 graphics) is not suspending / hibernating properly (see [here]("http://ubuntuforums.org/showthread.php?p=6040910")). I can, however, get it to turn off the display or shut down when I close the lid.

So what I want to do is configure my laptop to turn off the display when I close the lid -- and if I don't open the lid within 10 minutes, power down the machine. I've done some light shell scripting but have no clue where to start though with this. Any pointers?

---

### Post by ddrichardson on 2008-10-30
I *think* the power scripts are i /etc/acpi but I'll check.

---

### Post by ddrichardson on 2008-10-30
Yes, there's a guide to the files here - in Ubuntu its /etc/acpi/lid.sh

---

