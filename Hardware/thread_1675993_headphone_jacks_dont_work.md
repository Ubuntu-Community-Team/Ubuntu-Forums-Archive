---
title: "headphone jacks dont work"
date: 2011-01-26
forum: Hardware
---

### Post by killa7 on 2011-01-26
Hello I am using the latest version of ubuntu and i recently found out that my headphone jacks don't work on my Hp pavilion dv4 2045dx. If somebody could help that would be great.:confused:

---

### Post by coffee412 on 2011-01-26
> **killa7 said:**
> Hello I am using the latest version of ubuntu and i recently found out that my headphone jacks don't work on my Hp pavilion dv4 2045dx. If somebody could help that would be great.:confused:

Try firing up a term window and start alsamixer

> sudo alsamixer

Use F6 to select your video card and make sure the headphone jack is turned on and volume up.

coffee

---

### Post by killa7 on 2011-01-26
> **coffee412 said:**
> Try firing up a term window and start alsamixer



Use F6 to select your video card and make sure the headphone jack is turned on and volume up.

coffee

Didn't work but thanks

---

### Post by coffee412 on 2011-01-26
> **killa7 said:**
> Didn't work but thanks

Do you have the pulse volume control app installed? Check there to see if its selected or volume level.

---

