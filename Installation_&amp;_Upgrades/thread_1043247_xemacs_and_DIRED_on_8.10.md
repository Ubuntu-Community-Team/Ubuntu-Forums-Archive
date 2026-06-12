---
title: "xemacs and DIRED on 8.10"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2009-01-18
Installed xemacs on Ubuntu 8.10. Works in principle, but

1. all new 'dired' buffers have some extra stuff appended of the form
   //DIRED// 65 66 120 122 176 189 243 255 ...
   //DIRED-OPTIONS// --quoting-style=literal

2. when files are added/modified, the 'dired' buffer gets littered
   with extra text like
     -rw-r--r--  1 wfjm wfjm 11839 2009-01-18 16:37 new.txt//DIRED// 52 72
     //DIRED-OPTIONS// --quoting-style=literal
     //DIRED-OPTIONS// --quoting-style=literal

emacs works fine, no such effect. Any idea what is broken here ?
Thanks in advance for any hints.

---

### Post by marcpa on 2009-01-28
Set dired-use-ls-dired variable to nil.

One easy way is :

   M-x customize-variable RET dired-use-ls-dired

click mouse middle button on "Toggle" (to put it to off) and then click middle button on "State" and select "Save for future sessions".

--marcpa

---

