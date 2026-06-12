---
title: "dual boot help"
date: 2008-10-26
forum: General Help
---

### Post by linuxnoob40 on 2008-10-26
ok this has been covered before but the fix then doesnt work now.


i dual boot between windows and linux and i reformated windows and have no dual boot. so last time this happened i asked this question and got help this is what i did.



> Boot from the livd cd, open a terminal and:

Code:

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

Substitute results from find for (hdx,y) and setup (hdx).


now last time i did this it was hd0 now its hd4 and no matter what i do all that gets returned to me is

> grub> root (hdo,4)

Error 23: Error while parsing number

wtf am i doing wrong :confused:

---

### Post by lisati on 2008-10-26
Possible typo: make sure that you use hd0 with a number 0 "zero" and not a letter o "oh"

Hope this helps.

---

