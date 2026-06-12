---
title: "Switching from 10.10 to 11.04"
date: 2012-02-09
forum: Hardware
---

### Post by erikthedrink on 2012-02-09
In 10.10, I can still do mirror screens through an S-Video connection using a Intel Graphics Media Accelerator X3100 (shared). In 11.04, I cannot. I did a dual install of 10.10 and 11.04. I searched this forum yet no luck for mirror screens or X3100 which applies to the dilemma. I really like the 11.04 look though.:D

---

### Post by brpylko on 2012-02-09
I think you might want to use the program Disper. It can be installed by going to the terminal and typing

```
**sudo** add-apt-repository ppa:disper-dev/ppa
**sudo** add-apt-repository ppa:nmellegard/disper-indicator-ppa
**sudo** apt-get update
**sudo** apt-get install disper disper-indicator
```

You can then add disper-indicator to your startup applications.

---

