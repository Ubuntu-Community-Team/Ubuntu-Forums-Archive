---
title: "[SOLVED] Alt key in xterm"
date: 2008-11-29
forum: General Help
---

### Post by phorminx on 2008-11-29
Running emacs in an xterm gives me some trouble as the Alt (Meta) key is not recognized properly (using Ubuntu 8.10). Pressing Alt and some other ASCII key gives me non-ASCII characters like German umlaute on my US keyboard. So for some people this might be a feature for typing. But with emacs, it's more a bug. I do not have this problem when using the gnome-terminal instead of xterm. I found some bug report saying that terminfo for xterm was broken (Bug #148866). Yet it is beyond my knowledge whether this bug is actually talking about the same thing that bothers me.

---

### Post by phorminx on 2008-12-13
Update:

I have been using my ~/.Xresourses for many years on various unix/linux platforms. Somehow it contained the line

XTerm*eightBitInput:    true

Yet for ubuntu this flag should be set to false. Now the Alt key works in xterm as expected.

---

### Post by s0l1dsnak3123 on 2009-12-28
Thanks alot, this helped me :)

---

