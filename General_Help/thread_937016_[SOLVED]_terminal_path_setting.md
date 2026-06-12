---
title: "[SOLVED] terminal path setting"
date: 2008-10-03
forum: General Help
---

### Post by suhaib1thariq on 2008-10-03
how to set terminal path to /usr/bin

---

### Post by SteelWo1f on 2008-10-03
If you mean when you login you want to go to /usr/bin then you can just put an entry like 'cd /usr/bin' into the configuration script for your shell. If you're using base then put it at the end of your ~/.bashrc.

If you want it as part of your path then do `PATH=$PATH:/usr/bin`

---

### Post by mindoms on 2008-10-03
I'm curious...  why would you want to do that?

---

