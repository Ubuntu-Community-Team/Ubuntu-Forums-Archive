---
title: "sudo dpkg-reconfigure -a error"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by appoi on 2009-10-13
hi guys i need some help here, i am newbie to ubuntu and using ubuntu 9.04 jaunty.
when try type 

sudo dpkg-reconfigure -a

sudo dpkg-query: parse error, in file '/var/lib/dpkg/available' near line 2 package 'indicator-message':
value for status ' field not allowed in this context
/usr/sbin/dpkg-reconfigure:acl is not installed


can someone help me with this.....

---

### Post by Jimmyfj on 2009-10-13
I'm not sure that this will help you in any way, but try to switch to the root mode by typing

```
sudo su
```

And enter your admins password. Then type in the command

```
dpkg--reconfigure -a
```

Edit:
     Sorry - My bad - I didn't see that you wrote the command wrong. Look above for the right command.

---

### Post by Intrepid Ibex on 2009-10-13
Possibly running this:

```
sudo dpkg --configure -a && sudo apt-get -f install && sudo apt-get --fix-missing install && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by appoi on 2009-10-20
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `indicator-messages':
 value for `status' field not allowed in this context

---

