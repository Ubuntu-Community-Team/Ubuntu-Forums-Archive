---
title: "Radeon HD5450"
date: 2015-03-07
forum: Hardware
---

### Post by xeno74 on 2015-03-07
Hi All,

I bought an AMD Radeon HD5450 and I have some problems with it. With KMS I have a scrambled screen:

[ATTACH=CONFIG]260506[/ATTACH]

Without KMS (nomodeset) I have a black screen output. But xorg works in the background.

Any ideas?

Rgds,

Christian

---

### Post by Mark Phelps on 2015-03-07
Another kernel parm to try is "xforcevesa".  I found that to work when "nomodeset" did not do the trick.

---

### Post by xeno74 on 2015-03-08
> **Mark Phelps said:**
> Another kernel parm to try is "xforcevesa".  I found that to work when "nomodeset" did not do the trick.

Thank you for your answer. I tried it out today but unfortunately "xforcevesa" doesn't work. :-( Any other tips?

---

