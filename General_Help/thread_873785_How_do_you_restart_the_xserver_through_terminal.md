---
title: "How do you restart the xserver through terminal"
date: 2008-07-29
forum: General Help
---

### Post by Universal344 on 2008-07-29
I know this sounds stupid but I cant remember, how do you restart the      x server through the terminal.  Thanks!

---

### Post by Kevbert on 2008-07-29
Do you mean, press Alt-F2 and enter ```
/etc/init.d/gdm stop
```
followed by ```
/etc/init.d/gdm start
```

---

### Post by Separ on 2008-07-29
or just
```
sudo /etc/init.d/gdm restart
```:D

---

### Post by peakshysteria on 2008-07-29
Why not just use **CTRL + ALT + BACKSPACE** to restart X? I know the question was how to restart X when your in terminal. But anyways..... :)

---

