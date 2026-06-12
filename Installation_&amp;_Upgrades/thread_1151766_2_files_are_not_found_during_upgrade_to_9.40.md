---
title: "2 files are not found during upgrade to 9.40"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by nubenirik on 2009-05-07
Hello,
while i was upgading to 9.40 from 8.10, the uograde manager reported
that 2 files namely:
1. Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb) 404 Not Found

2. Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.9.04.1_i386.deb) 404 Not Found

How can i download those files?
thanks

---

### Post by HyRax on 2009-05-07
Missing files happen occasionally because the package list for that mirror was updated before the files references by that list were copied to that server.

I was going to say "switch to a more reliable mirror" but you're using the main one already. Give it a few hours and try again.

---

### Post by nubenirik on 2009-05-08
I have been waiting for 2 days but no luck.
Does anybody know where else can i find these files?
or is there any ways of doing it through the console?

thanks

---

### Post by HyRax on 2009-05-08
I just checked my own mirror - that file does not exist anymore - it has been succeeded by a newer version.

Run a **sudo apt-get update** and then try to do that component update again - you should get the slightly newer version instead now.

---

