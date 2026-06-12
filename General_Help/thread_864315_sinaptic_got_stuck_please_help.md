---
title: "sinaptic got stuck please help"
date: 2008-07-19
forum: General Help
---

### Post by roberto.eiberle on 2008-07-19
I start sinaptic and it tells me to run manually, result is the following terminal dump where it intends to stay forever, it has been running for over 2 hours with no change, everything else fine, running gutsy




roberto@roberto:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
roberto@roberto:~$ sudo dpkg --configure -a
[sudo] password for roberto:
Setting up language-support-ja (1:6.06+20060529) ...
Generating locales...
  ja_JP.UTF-8...

---

### Post by unutbu on 2008-07-19
What happens if you type

```
sudo apt-get purge language-support-ja
```

The above command will try to uninstall language-support-ja, a package that provides Japanese language support. If you want this package installed, 
try reinstalling it after your purge it by typing

```
sudo apt-get install language-support-ja
```

---

### Post by roberto.eiberle on 2008-07-20
worked o.k. thank you for your help

---

