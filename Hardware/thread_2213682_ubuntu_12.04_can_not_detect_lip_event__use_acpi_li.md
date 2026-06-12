---
title: "ubuntu 12.04 can not detect lip event  use acpi_listen,but  win7 works well"
date: 2014-03-28
forum: Hardware
---

### Post by liu3 on 2014-03-28
1. acpi_listen can not detect lid event  .
2.close lid--->open lid---> press  powerbutton to make a suspend--->powerbutton again for resume: then  both lid event and powerbutton event  can be
 detected with acpi_listen.
 3.Though acpi_listen can not detect lid event,the lid state (cat proc/acpi/button/lid/LID0/state) is right ,and can be change when lid close/open.

os version: ubuntu 12.04

Is it a bug&#65311;what should I do ?

---

