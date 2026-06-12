---
title: "[SOLVED] apt-get is crazy !?"
date: 2008-07-22
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-07-22
I installed transmission v1.22 from .deb (got it from getdeb.net)
The next time I use apt-get it says:
```
[boris: ~]$ install scrot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
scrot is already the newest version.
The following packages were automatically installed and are no longer required:
  transmission-common transmission-gtk
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
[boris: ~]$
```
:lolflag:
After apt-get autoremove it removes transmission and I have to install it again... It's really annoying!

Anyone have the same problem, or can you reproduce it? Please, any help will be much appreciated!

Edit: **install** is alias for `sudo apt-get install`

---

### Post by Gunman1982 on 2008-07-22
Thats not really a problem, its just telling you that it can't find those two packages in the repos and hence it assumes they are not needed anymore. Just don't execute an apt-get autoremove and you should be fine.

If it puzzles you that apt-get didn't install your scrot (whatever that is) the line 
'gshutdown is already the newest version.' is apt-get's response to your try.

---

### Post by LinuX-M@n1@k on 2008-07-22
> **Gunman1982 said:**
> Thats not really a problem, its just telling you that it can't find those two packages in the repos and hence it assumes they are not needed anymore. Just don't execute an apt-get autoremove and you should be fine.

If it puzzles you that apt-get didn't install your scrot (whatever that is) the line 
'gshutdown is already the newest version.' is apt-get's response to your try.

Thanks for the reply.

I was going to install 'gshutdown', but I renamed the command to 'scrot' (here, in my post) :D. I forgot to rename 'gshutdown is already the newest version.' to scrot too :lol:

Anyways, apt-get installs everything, but what it says about transmission is really annoying me. Thank you for the help though ;).

---

### Post by LinuX-M@n1@k on 2008-07-22
Hey, I have a solution!
```
sudo aptitude hold transmission-{common,gtk}
```
This holds the packages, so they can't be removed or upgraded ;). Result:
```
[boris: ~]$ clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[boris: ~]$ 
```

---

