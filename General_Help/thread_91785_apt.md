---
title: "apt"
date: 2005-11-18
forum: General Help
---

### Post by bfarris on 2005-11-18
I have a package which has something wrong with it so that it can't be fully installed, and apt just hangs trying to install it.  The package is win32codecs and it is hanging at:
 Resolving www1.mplayerhq.hu... 192.190.173.45
Connecting to www1.mplayerhq.hu|192.190.173.45|:80... connected.
HTTP request sent, awaiting response...

I don't need the package installed because I have win32codecs working fine.  I just need to cancel this installation so that I can use apt again.

thanks

---

### Post by 23meg on 2005-11-18
"sudo apt-get -f install" should work. (note: please avoid opening multiple threads for the same problem).

---

