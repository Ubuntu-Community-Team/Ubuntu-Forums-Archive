---
title: "Can't Download Updates"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by bluec10 on 2008-12-21
I haven't done updates for a while.  Yesterday I ran updates with my Ubunto 8.04 machine.  I had about 80 updates and it took a long time.  I'm down to my last 8, but every time the machine attempts to get updates I get the following message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.18.2-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.18.2-1ubuntu2.1_i386.deb)
  404 Not Found

I have internet access and all the other updates worked.  I'm working as administrator.  What is happening?

bluec10

---

### Post by 2hot6ft2 on 2008-12-21
The package may have been updated and it's trying to get the old one that's not there anymore. Try

Applications>Accessories>Terminal
and enter
```
sudo apt-get update
``` then close the terminal after it finishes and returns you to the prompt and go to 
System>Administration>Synaptic Package Manager
click on reload then Mark All Upgrades then Apply
That should take care of it.

---

### Post by Kevbert on 2008-12-21
You may need to change your server in Software Sources.

---

### Post by bluec10 on 2008-12-21
Thank-you.  Problem solved.

---

