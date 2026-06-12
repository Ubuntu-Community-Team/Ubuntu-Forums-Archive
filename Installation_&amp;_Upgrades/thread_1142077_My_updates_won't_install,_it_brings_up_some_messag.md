---
title: "My updates won't install, it brings up some message?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by dizzygamr on 2009-04-28
What I'm doing is clicking the little update notification icon in the status bar (the bar with "applications, places, system") and when it brings up the update manager it looks fine. Then I click "install updates" and I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running dpkg --configure -a  and it gave me: 

dpkg: requested operation requires superuser privilege

What do I do?

---

### Post by kostkon on 2009-04-28
You need to give it like this
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

For more info about *sudo*, check [here]("https://help.ubuntu.com/community/RootSudo"), if you want.

---

### Post by dizzygamr on 2009-04-29
Thanks for that tip, but now it won't install 6 updates (mainly firefox updates if that helps) and it gives me this error message: 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.9+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.9+nobinonly-0ubuntu0.8.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.9+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.9+nobinonly-0ubuntu0.8.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.9+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found

---

### Post by Partyboi2 on 2009-04-29
Try reloading the package list if that does not work then try changing your download server in Software Sources (System>Admin>Software Sources>1st Tab) to a different one then the one you are currently using.

---

### Post by upchucky on 2009-04-29
click System > Administration > Software Sources

enter the password

make sure all the little boxes are checked and the source says Main Server

close the window then do update again

---

