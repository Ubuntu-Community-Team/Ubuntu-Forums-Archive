---
title: "How do I Install windows on a second partition?"
date: 2008-09-21
forum: General Help
---

### Post by bakaeigo on 2008-09-21
I have a single-boot system running Hardy, and I want to dual-boot with Windows (for gaming use). How can I install windows without messing up my Ubuntu partition?

---

### Post by geeth on 2008-09-21
You will need to have an empty partition to install windows on.
It will write it's own boot loader so after you windows install you will have to boot from ubuntu's live cd and re-install grub so you can boot into linux again.

Also you will have to add windows into you menu.lst with grub to be able to boot into that after you have re-installed grub.

---

