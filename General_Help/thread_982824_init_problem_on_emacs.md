---
title: "init problem on emacs"
date: 2008-11-15
forum: General Help
---

### Post by yexilein on 2008-11-15
Hello,

When I start emacs, there is an error message:
"An error has occurred while loading `/home/stephan/.emacs':

File error: Cannot open load file, xfonts"
even if it seems that I already installed this package.

Then the program starts and everything seems to be normal, the only problem being that I can't customize emacs, because "there was an error while loading init file".

I tried to install several other packages related to xfonts, but nothing changed.

Thanks for help!

---

### Post by renenel on 2009-01-22
It seems like you have an old emacs config file on a new Ubuntu machine. The following worked for me with the same problem:

Edit (VI, kwrite, or emacs :)) the following file ~/.gnu-emacs.

Change this line:
(if (> emacs-major-version 20) (require 'xfonts))

To:
(if (> emacs-major-version 20) (require 'xfonts-base))

Hope it works,
Renen

---

