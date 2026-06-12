---
title: "Set display"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by ajay12325 on 2009-08-21
Dear All,

I am getting error , Display not set! Set Display first , while trying to start Oracle Installer. Please guide me how to tackle with same. I am getting error while trying 
# xhost +


Regards
Ajay

---

### Post by lemming465 on 2009-08-26
The last time I installed oracle was a while ago, but it ran as a GUI.  Under X windows there should be an environment variable DISPLAY pointing at some X screen such as 0.0.  How are you launching the installer?  I suggest *gksu ...* or *sudo bash*.  Using plain "su" to become root will probably wipe out your environment variables when it simulates a text console login.

---

