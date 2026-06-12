---
title: "[SOLVED] Please help to configure ipython in Emacs"
date: 2008-11-14
forum: General Help
---

### Post by dmitrijledkov on 2008-11-14
Heya! I've started to use scipy and I really want to use ipython in an emacs buffer. I have pymacs, emacs-snapshot and ipython installed.

I've added this to ~/.emacs
```

(require 'ipython)
(setq py-python-command '("/usr/bin/ipython"))
(setq py-python-command-args '("-pylab" "-colors" "LightBG"))

```

But when I do M-x python-shell it still says using CPython shell. I did save .emacs and I did restart the computer.

Could you please help me? Thankyou.

---

### Post by dmitrijledkov on 2008-11-14
Solved it.

I had to install python-mode and then do this in my ~/.emacs
```

(autoload 'python-mode "python-mode" "Python Mode." t)
(add-to-list 'auto-mode-alist '("\\.py\\'" . python-mode))
(add-to-list 'interpreter-mode-alist '("python" . python-mode))


(require 'ipython)
(setq py-python-command '("/usr/bin/ipython"))
(setq py-python-command-args '("-pylab" "-colors" "LightBG"))

```

---

