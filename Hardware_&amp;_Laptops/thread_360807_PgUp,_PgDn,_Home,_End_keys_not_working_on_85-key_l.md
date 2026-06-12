---
title: "PgUp, PgDn, Home, End keys not working on 85-key laptop keyboard"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by jim0203 on 2007-02-13
I've been using Ubuntu ver happily on my Toshiba Portege 2000 for a few weeks now. The only problem is that the PgUp, PgDn, Home and End keys don't do anything (it's an 85 key keyboard). I've tried changing the keyboard layout, but couldn't find any for 85 key keyboards (I tried the one for another Toshiba, but that didn't do the trick) and have tried Google etc for the last hour, with no joy.

Does anyone have any suggestions?

Thanks in advance!

Jim

---

### Post by tgalati4 on 2007-02-20
You got taken.  Most pc's have 104 keys.

Try a key code capture to see if the navigation keys are putting out anything.
If you can get the codes, then you can remap the keys in Ubuntu to anything you want.  There are several tools.

For instance xev will give:  ^[[A^[[B^[[D^[[C  when hitting the arrow keys.

showkey -u will also reveal key codes.  If you don't get codes then you can't remap them.  

Try asking on a Toshiba Laptop forum, there must be others who got shortchanged.

---

