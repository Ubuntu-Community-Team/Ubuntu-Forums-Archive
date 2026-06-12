---
title: "[SOLVED] Vim: syntax highlighting for bash files"
date: 2008-11-22
forum: General Help
---

### Post by abcuser on 2008-11-22
Hi,
I would like to enable syntax highlighting for bash files, just like gedit has when I save file with .sh file extension.

From the following link it looks like it is possible:
[http://www.cyberciti.biz/faq/wp-content/uploads/2008/05/show-line-numbers.png](http://www.cyberciti.biz/faq/wp-content/uploads/2008/05/show-line-numbers.png)

How to enable syntax highlight for bash scripts in vim program?

Regards,
Abcuser

---

### Post by x1a4 on 2008-11-22
Hi,
Inside vim do
```
:syntax on
```

To make the change permanent add
```
syntax on
```
to your ~/.vimrc file

---

