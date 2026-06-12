---
title: "acpi suspend to ram not working in breezy"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by chunk on 2005-10-20
I upgraded to breezy from hoary and acpi suspend to ram is no longer working.

Can someone tell me which log(s) I should check to troubleshoot the problem?

---

### Post by Lambert on 2005-10-20
with your favorite text editor, open up /etc/default/acpi-suppport and remove the # from the second line should say```
acpi_sleep=true
```

---

### Post by chunk on 2005-10-22
[QUOTE=Lambert]with your favorite text editor, open up /etc/default/acpi-suppport and remove the # from the second line should say```
acpi_sleep=true
```[/QUOTE]

Yup, that did the trick. Thanks.

---

