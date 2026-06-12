---
title: "[SOLVED] Can't view any webpages in firefox, but have internet connection"
date: 2008-08-03
forum: General Help
---

### Post by cszikszoy on 2008-08-03
Hello,
 
I'm having a very strange problem with Firefox.  I can't view any webpages in firefox, but I know that I have a connection to the internet.  I'm currently posting on the same computer from within virtualbox, where the internet works fine.
 
In console, I can ping external websites without any problem.  I've tried moving my configuration folder under ~/.mozilla/firefox, and have even tried uninstalling then reinstalling firefox.  For whatever reason, it simply wont load a single webpage.
 
Oh, i've also disabled ufw, but as I said before, browsing the internet from within a virtual machine works fine.
 
Any help is appreciated!!  Thanks.

---

### Post by cszikszoy on 2008-08-04
Sorry to bunp, but I'm hoping someone can help!

---

### Post by cszikszoy on 2008-08-04
anyone?

---

### Post by mb_webguy on 2008-08-04
Try starting Firefox from the terminal, and see if there's any output...

---

### Post by cszikszoy on 2008-08-04
Firefox forks immediately, shows no output.

I've actually solved it.  I was trying to use a different DNS server.  Somehow (???) this changed my proxy settings in gnome.  After I changed these back to normal everything is fine again.

Thanks though!

---

