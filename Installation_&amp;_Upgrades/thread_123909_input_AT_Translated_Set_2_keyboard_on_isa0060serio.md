---
title: "input: AT Translated Set 2 keyboard on isa0060/serio0"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by yusufk on 2006-01-31
When installing Ubuntu, the install process may stall showing the last line:
input: AT Translated Set 2 keyboard on isa0060/serio0

On my pc, the problem turned out to be that I did not have enough RAM (64MB min). The line before that sets up the RAM disk, which I suspect leaves very little ram for anything else if one has less than 64MB ram.

Hope this helps anyone with the same problem.

Yusuf

---

