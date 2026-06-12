---
title: "Full restricted ATI drivers install"
date: 2008-10-08
forum: General Help
---

### Post by imbjr on 2008-10-08
I was reading:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and noticed for Hardy a couple of commands to run after enabling the restricted ATI drivers:

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

Now, I believe, I've never entered those commands before and I am tempted to do so now so as to get better Compiz performance. But if things go wrong - how do I undo the above commands?

---

### Post by chaosdesigner on 2008-10-08
backups

Thats always a way to be sure, look at the code and make a backup of all the Files that are named in the command. You can also backup xorg.conf since your messing with drivers.

I would also try to understand what this command does so maybe google it.

---

