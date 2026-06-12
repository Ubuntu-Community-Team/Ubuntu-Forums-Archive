---
title: "[SOLVED] /usr in Trash"
date: 2008-07-22
forum: General Help
---

### Post by Cobalto on 2008-07-22
While trying to sort out some problems with VMWare, I mistakenly did the following:

> sudo rm -r /usr vmware*

Yes, I know I'm an idiot. 

Is there a way to restore /usr from Trash, or to reinstall Gnome to get the machine to a usable state? Any other ideas? 

If I could get even Nautilus and sudo to work again, it would be enough.

Thanks!

Cobalto

---

### Post by Separ on 2008-07-22
EDIT back: It cannot be recovered as rm does not move to trash. :-|
What you might be able to do is boot the ubuntu Live CD and copy the /usr folder from that over onto your drive.

For future reference, add this to the ~/.bashrc file:
```
alias rm='rm -i'
```
It asks you to confirm the remove.

---

### Post by Cobalto on 2008-07-23
That was brilliant. Thanks, mate.

---

