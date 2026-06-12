---
title: "help with xorg server disabled"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by locke42069 on 2006-07-03
I was following the instructions on installing xgl and compiz. I got to a point to where i needed to modify the xorg server. I modified the server and was told to restart. I did and it will boot up butthe xorg server has a problem and i can no longer boot into the gui. it allows me to login in text mode. im pretty sure i know what i need to undo but i do not know how to get to the file to fix it. the file is /etc/gdm/gdm.conf-custom. here is the link mentioned above [http://ubuntuforums.org/showthread.php?t=145068&highlight=xgl+ati](http://ubuntuforums.org/showthread.php?t=145068&highlight=xgl+ati). At the moment i am logged into windows and want to get back to ubuntu as soon as possible. i am still new with linux and can use any help possible.

---

### Post by woedend on 2006-07-03
so do you suspect its xgl related or xorg related?
to undo the xgl part, in gdm.conf-custom remove everything after the line
[servers]

---

