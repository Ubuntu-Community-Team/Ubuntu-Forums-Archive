---
title: "[SOLVED] Comparing two text files"
date: 2008-11-04
forum: General Help
---

### Post by Kevbert on 2008-11-04
Is there any terminal command to compare two text files and output the result to a new file ?  I specifically want to compare two package lists to see the changes on my PC for Jaunty Jackalope.

---

### Post by taurus on 2008-11-04
Maybe something like

```
diff file_1 file_2 > difference
```

---

### Post by Kevbert on 2008-11-04
Thanks taurus. That's exactly what I was after. 39 updates so far with Jaunty Jackalope when compared with Intrepid Ibex.

---

