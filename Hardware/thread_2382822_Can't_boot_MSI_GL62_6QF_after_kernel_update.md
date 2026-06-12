---
title: "Can't boot MSI GL62 6QF after kernel update"
date: 2018-01-17
forum: Hardware
---

### Post by olegorov on 2018-01-17
After kernel update from 4.13.0-24 to 25 (and then to 29 and 30) Ubuntu 17.10 on my laptop MSI GL62 6QF freezes at boot logo. If I choose kernel 24, Ubuntu boots normal. I attached syslogs for kernels 24 and 29.

Solved. Thanks to all answers. This string helped me: [COLOR=#000000][FONT=&quot]sudo apt install --reinstall shared-mime-info[/FONT][/COLOR]

---

