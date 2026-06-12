---
title: "How to fix the font rendering in hardy ??"
date: 2008-07-16
forum: General Help
---

### Post by el-mar01 on 2008-07-16
Hi,

When I upgraded to hardy heron (I did a clean install) my fonts are slightly blurry and they don't look very good .. I used the Segoe UI font on Gusty and it was really beautiful now in Hardy they look pretty crap .. I have tried to change all the font settings in the appearance settings but it wont fix the problem.

Thank you !!

---

### Post by el-mar01 on 2008-07-17
*bump*

---

### Post by benerivo on 2008-07-17
You could try```
sudo dpkg-reconfigure fontconfig-config
```which I think goes a little deeper in to the font rendering than the font options window does. Once you've set some options, the run```
sudo dpkg-reconfigure fontconfig
```and log out and back in again.

EDIT - There's been a [good thread]("http://ubuntuforums.org/showthread.php?t=800724") recently on fine tuning fonts.

---

