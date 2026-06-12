---
title: "[SOLVED] Hardy on Inspiron 1525, keyboard Issues"
date: 2008-04-28
forum: Hardware
---

### Post by xand on 2008-04-28
Hi,
Got a fresh Hardy install with the alternate CD, for the pt-br language (the keyboard has a pt-br kind of layout too), and everything seemed to work fine, even the multimedia buttons of the laptop.

However i noticed that the type ahead function in nautilus was not working, i mean when you start typing a string and it focus the first file which matches it.

So i uninstalled the packages scim, scim-bridge-agent, scim-bridge-client-gtk and scim-gtk2-immodule, and the type ahead worked again. Unfortunatly this way, if i try to get for instance a "é", it gives me a "'e".

Any work arrounds ?
Thank you

---

### Post by xand on 2008-04-28
Fixed. I followed the steps on [http://ubuntuforums.org/showthread.php?t=757070&highlight=scim](http://ubuntuforums.org/showthread.php?t=757070&highlight=scim) , with the extra step of deleting .scim and .xinit.d folders before restarting X.

:)

---

