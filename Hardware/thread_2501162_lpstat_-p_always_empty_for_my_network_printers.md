---
title: "lpstat -p always empty for my network printers"
date: 2024-09-25
forum: Hardware
---

### Post by pol2095 on 2024-09-25
Hello,


I have 2 HP network printers that appear in settings > printers, however when I click on the 3 small dots > Use as default printer, my selection never take.
"lpstat -p" returns an empty list and when I try to print with Thunderbird for example, no printer appears in the list.


I also have Ubuntu installed on an RPI so ARM64 and there everything works fine.


How can I repair my Ubuntu 24.04 x64?
Thanks

Solved : I uninstalled and reinstalled CUPS, it work now.

---

