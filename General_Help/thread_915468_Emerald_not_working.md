---
title: "Emerald not working"
date: 2008-09-09
forum: General Help
---

### Post by enzodad on 2008-09-09
emeralds not working. i went ti advanced desktop and for window decoration its./usr/bin/compiz-decorator.
I even did the alt f2 compiz --replace.
i have a theme its just does nothign when i select it. and yes my effects are set to full so its on ..

---

### Post by tuxxy on 2008-09-09
How did you install emerald

---

### Post by enzodad on 2008-09-09
sudo apt-get install compizconfig-settings-manager emerald

---

### Post by fooman on 2008-09-09
try this:

open compiz config settings manager (system > preferences > compiz config settings manager).  in the left hand column, click on "effects".  on the right,  put a check next to "window decorations" and then click on the icon for that selection. on the page that opens,  find the "command" line,  delete whatever is in the box and replace with:

```
emerald --replace
```

restart x (alt-ctrl-backspace)

---

### Post by enzodad on 2008-09-09
Hey thanks worked like a charm :)

---

