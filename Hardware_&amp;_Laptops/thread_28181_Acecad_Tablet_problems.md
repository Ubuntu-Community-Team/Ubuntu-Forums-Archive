---
title: "Acecad Tablet problems"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by yoni on 2005-04-19
Hello, I'm quite new to ubuntu and I like it alot :)
Everything seems to be working fine, except my acecad tablet (a tablet is this board with a graphic pen the you can use to draw instead of using the mouse).
I was previously working under mandrake 10.1, in which I was able to get my acecad working using the xorg driver from over here: [http://perso.wanadoo.fr/septieme/acecad/xfree.html](http://perso.wanadoo.fr/septieme/acecad/xfree.html)
I didn't need to patch my kernel or anything like that.
I've done the same steps on ubuntu, and it doesn't seem to work ..
After compiling the driver (acecad.o) and it being copied to the directory it should have, I've edited the xorg.conf file as explained in the tutorial, added an InputDevice for the acecad tablet, and added it to the ServerLayout part.
Everything as its written in the tutorial, and yet the tablet doesnt work ...
Any ideas ?
Maybe I should patch my kernel ?

Thanks ahead.

---

### Post by yoni on 2005-04-19
Another thing I should mention - 
When compiling the driver, I had to delete a bit of the code in order for it to work.
The code that code issues was "if kernel version < 2.6 then ...", and altough my kernel version is greater than 2.6 (2.6.10) it entered that part of the code, which caused problems, so i deleted that part and then it compiled fine.

---

### Post by yoni on 2005-04-19
Anyone at all ?
Maybe a suggestion as for where should I ask if not over here ?

---

### Post by yoni on 2005-04-21
[QUOTE=yoni]Anyone at all ?
Maybe a suggestion as for where should I ask if not over here ?[/QUOTE]
 hmmmm ? *bump*

---

### Post by 4ebees on 2005-10-12
Hi there,

I've got the same problem with a Dolphin Tablet (it's a clone of Aiptek).

I can't get it to work in Ubuntu - which is sad :(

but it works fine in Fed Core (I'm using 3) and SimplyMepis.

If anyone can help with this, I agree, it would be BRILLIANT, as I very much like Ubuntu and the philosophy behind it.

---

