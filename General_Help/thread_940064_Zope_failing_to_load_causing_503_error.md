---
title: "Zope failing to load causing 503 error"
date: 2008-10-06
forum: General Help
---

### Post by rugbert on 2008-10-06
I migrated a server from one machine to another (using this thread: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) and while most everything transferred over correctly (some permission settings didnt) apache isnt %100 working. 

There are two virtual host files, the default, and the mysite.test.com. and Mysite is using zope for all the web stuff. At first, apache would only server the default virtualhost file, but I disabled it and now I get a 503 error. Im assuming zope is failing to load correctly, how can I fix this?


edit - I found this in the error log:
> 
127.0.0.1 - - [07/Oct/2008:05:27:41 -0500] "GET / HTTP/1.0" 503 323 "-" "Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c (internal dummy connection)"


---

### Post by rugbert on 2008-10-07
derp

---

