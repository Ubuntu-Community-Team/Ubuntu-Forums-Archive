---
title: "[SOLVED] Unable to install or update..."
date: 2008-12-02
forum: General Help
---

### Post by aprashanth on 2008-12-02
when i am trying to install or update any file i am getting an error..
as below.. please help me to fix this..


root@tsrinu-desktop:/media/cdrom/Mathematica-6_linux/Unix/Installer# sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@tsrinu-desktop:/media/cdrom/Mathematica-6_linux/Unix/Installer#

---

### Post by HalPomeranz on 2008-12-02
So have you tried doing what the error message suggests and running "sudo dpkg --configure -a"?  That would seem to be a good first step...

---

### Post by aprashanth on 2008-12-02
thank you..
it worked.. actually i am trying to install mathematica..

---

