---
title: "Can't Install vcl"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by dsrr47 on 2009-01-30
hey, 
  I'm pretty new to ubuntu and when ever i try to install vcl through the terminal using the command "apt-get install vcl" I get the message 

"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

Any idea what is causing this and how I can fix it. 

Cheers

---

### Post by taurus on 2009-01-30
You need to include a sudo in front.  And by the way, are you wanting to install vlc (or vcl)?

```
sudo apt-get update
sudo apt-get install vlc
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dsrr47 on 2009-01-31
Vlc sorry typo. and that solved my problem thank you much!

---

