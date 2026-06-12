---
title: "Bug and Solution - color in Emacs Shells"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by ceb004 on 2008-12-20
I recently upgraded to 8.10 to take advantage of new drivers in the kernel, and noticed that someone had decided to set the default .bashrc to alias ls to 'ls --color=auto' unless the calling terminal was set to 'dumb'.  

When installing emacs, and using the shell feature within that application, this leads to ANSI ESC-[ garbage on ls output, unless one also includes 
the following in /usr/local/share/emace/site-lisp/default.el:

(add-hook 'shell-mode-hook 'ansi-color-for-comint-mode-on)

It would seem sensible to add this to the package distribution -- I hope that posting this here will get this to the right person.

---

