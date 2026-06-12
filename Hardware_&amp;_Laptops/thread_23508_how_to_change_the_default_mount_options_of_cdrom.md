---
title: "how to change the default mount options of cdrom?"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by witkey on 2005-04-02
Hoary RC

Locale is zh_CN.utf8

When I insert a data-cd to the cdrom, gnome-volume-manager auto mount it with a wrong iocharset. So, the content of cd can't display properly .

I want to know where can I change the default iocharset of the cdrom.

I have google on the net , follow the hint by change the setting in storage.policy . But it dosn't work in hoary.

Any help is appreciated!

---

### Post by soul_rebel on 2005-04-03
the options should go in /etc/fstab, but i can't tell actually how to change the charset. Also consider that cdrom filesystem may not accept any encoding.
bye

---

