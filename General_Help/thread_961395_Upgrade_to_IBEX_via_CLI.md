---
title: "Upgrade to IBEX via CLI?"
date: 2008-10-28
forum: General Help
---

### Post by CyberCowboy on 2008-10-28
I know that after IBEX is released I can upgrade a hardy install via the apt-get dist-upgrade but is there a script I can run that will upgrade me to the beta repos via command line?

The reason I ask is that I'm presently at work and would like to have my home PC upgrade during the day so that I can test tonight.  I did a Wake-on-lan so AFAIK there is no way for me to graphically log in remotely because VNC doesn't start until after it's logged in.

---

### Post by SoCalChris on 2008-10-28
```
sudo do-release-upgrade -d
```
I did the same thing, upgraded my son's and wife's computers while at work.

---

### Post by CyberCowboy on 2008-10-28
> **SoCalChris said:**
> ```
sudo do-release-upgrade -d
```
I did the same thing, upgraded my son's and wife's computers while at work.

Much thanks, I've got it started now.

---

### Post by SaltySurfer on 2008-11-08
Hmm, here's a funny question: Anyone know what happens if you start the CLI upgrade over SSH and the connection breaks on the client side?  

Would the upgrade continue to run on the server?

---

### Post by sapg on 2008-11-20
You could use "screen".

---

