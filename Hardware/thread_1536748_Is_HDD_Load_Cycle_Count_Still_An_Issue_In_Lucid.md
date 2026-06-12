---
title: "Is HDD Load Cycle Count Still An Issue In Lucid?"
date: 2010-07-22
forum: Hardware
---

### Post by chris1379 on 2010-07-22
I thought I read somewhere that this had been solved in Lucid. See [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
for reference. I left my laptop on overnight (10 hours) and the Load Cycle Count increased from 94931 to 95914. Should I be worried? I see that laptop-mode-tools is not installed by default. Should I install it?

---

### Post by dabl on 2010-07-22
It's not that simple.

[https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux](https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux)

---

### Post by stchman on 2011-02-01
I just installed Lucid on my Toshiba and the cycle count increased about 8 in the last 20 minutes.

The count goes up much less on AC.

```

bob@kronos:~$ sudo smartctl -d ata -a /dev/sda|grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   094   094   000    Old_age   Always       -       62176

```

---

