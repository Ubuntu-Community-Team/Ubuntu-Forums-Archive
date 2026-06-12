---
title: "&quot;unable to access document&quot; error in lynx"
date: 2008-09-13
forum: General Help
---

### Post by machinakias on 2008-09-13
hello folks! i need some help with a strange error i get when i try to launch lynx in my ubuntu 8 server.It says "unable to access document" and then "can't access file://localhost/usr/share/ubuntu-artwork/home/index.html".
Then it returns me to the command prompt...tried to remove and reinstall lynx,tried re install my ubuntu from scratch but no luck.
Any ideas?:confused:

---

### Post by javaJake on 2008-09-13
It's telling you that /usr/share/ubuntu-artwork/home/index.html does not exist, or perhaps that you don't have permissions to read that file (which would be odd). I assume the reason it tries to get this file is because that is what lynx's homepage is set up as.

A quick and easy solution is to run lynx with a web address instead of just saying "lynx", for example: ```
lynx google.com
```

---

