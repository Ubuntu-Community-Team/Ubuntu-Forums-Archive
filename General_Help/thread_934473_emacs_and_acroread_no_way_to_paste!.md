---
title: "emacs and acroread: no way to paste!"
date: 2008-09-30
forum: General Help
---

### Post by mcopelli on 2008-09-30
Hello, 

I have done some considerable browsing before asking for help in this forum. I love emacs, and I love acroread. But they don't seem to love each other: if I copy some content from acroread, then I just can't paste the contents onto emacs. 

Following some advice found elsewhere, I learned that by adding 

(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

to my .emacs, emacs finally recognized text copied to the clipboard from *almost* any application (say, firefox), but *not* from acroread. 

Has anybody found the solution for this nightmare?

Thanks, 

Mauro Copelli

---

### Post by ieBrazil on 2008-09-30
Good luck! Just cant help ya. I'm just coming on Ubuntu... 'm here to learn!

---

