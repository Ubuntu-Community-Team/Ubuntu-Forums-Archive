---
title: "[SOLVED] Hardy isn't giving me the option to upgrade to Ibex, how do I do it manually"
date: 2008-11-01
forum: General Help
---

### Post by fullmetalgerbil on 2008-11-01
I just tried using my update manager to upgrade to Ibex. Checked for updates, all it said was my system is up to date-nothing about a new release being available. Of course, I have the Ibex installation media on hand, but I was hoping I'd not have to f-disk and do a whole fresh install.
I know there's a way to do upgrades outside the update manager, I just don't know the commands. 
If only it were as simple as sudo apt-get Intrepid Ibex.

---

### Post by taurus on 2008-11-01
If you pop in the CD, 8.10, you would see a menu that gives you an option to upgrade your machine.  Otherwise, here is a link on how to from Hardy.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by fullmetalgerbil on 2008-11-01
Got it. Thanks!

---

### Post by notoriousdbp on 2008-11-01
Hardy won't instantly recommend upgrading to 8.10 as Hardy is a long term support release.  You can, however, open a terminal and type in

```
gksu "update manager -c -d"
```

and update manager should then let you know that 8.10 is available.

---

