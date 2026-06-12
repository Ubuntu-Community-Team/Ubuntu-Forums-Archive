---
title: "Need Graphics Accelerator on Toshiba L300 (Gutsy in)"
date: 2009-02-21
forum: Hardware
---

### Post by amkr on 2009-02-21
I cant do desktop effects and stuff. I cant also install my Graphics drivers on Ubuntu. Where will I get the Ubuntu versions?

---

### Post by sigixv on 2009-05-31
L300 has intel graphics. These are blacklisted. If you want to enable desktop effects, you have to bypass compiz-driver check

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

