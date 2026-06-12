---
title: "Upgraded to Jaunty: now inPHPmyadmin, can't log in as root (but I can in other GUIs)"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by leenwebb on 2009-04-27
I upgraded to Jaunty over the weekend and now I can't log in to PHPmyadmin as root.

I can log in as root (with no/blank password*) through the command line and other GUIs (so I know the password -- or lack thereof -- is correct), AND I can log in as other DB users through PHPmyadmin (so it's not that the whole PHPMyAdmin program/interface is broken).  

* I know, I know... but it's my own personal dev machine and not accessible via the web.

But I like PHPMyAdmin and would like to be able to log in as root there in order to create new databases and whatnot.

Thoughts?  Thanks!

---

### Post by zoomzoom833 on 2009-04-30
I had the same problem on two machines. My password was blank, and I fixed it by setting one.

I think phpmyadmin might be balking on the blank password

---

### Post by unco on 2009-05-03
I have same problem, having just setup new install of Xubuntu Jaunty.  The exact same setup process on Ibex works fine.

Problem: try to log into phpmyadmin as root (blank password) just gives 'Access denied'.

Tried: login to phpmyadmin as phpmyadmin (blank password) and gets in fine.  So not related to blank password.

Can login to MySQL Admin GUI using root (blank password).

Any ideas?

---

### Post by Jonne on 2009-05-14
[this](http://ubuntuforums.org/showpost.php?p=1476548&postcount=5) post saved my bacon, in case you people are still wondering how to fix it.

It seems like phpmyadmin REQUIRES a password, so you just set one, no matter how easy.

---

