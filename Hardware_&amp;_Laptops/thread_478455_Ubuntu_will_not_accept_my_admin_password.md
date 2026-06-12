---
title: "Ubuntu will not accept my admin password"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by jlightl on 2007-06-19
So while trying to get my broadcom wireless card to work in my HP laptop I have noticed that I am unable to perform any administrative (i.e. manual network connection, windows wireless drivers) tasks graphically using the root password. However, I can login and perform as root via terminal by typing "su" and I can change the root password by typing "sudo passwd root" but I can't do anything graphically. Any help would be appreciated.

---

### Post by warcriminal on 2007-06-19
Try the gksudo command.

[http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO](http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO)

It may allow you to do what you need to with your wireless card.

---

### Post by jlightl on 2007-06-19
thanks but it still prompts me for my admin password and still does not accept it. I had my wireless card working on a universities network but not my home network. after setting a root password and removing some abilities from my user account I was unable to connect to any network ( the card is detected but not powering on). Is there a way I login as the root to perform tasks or should I just start over.

---

### Post by jay019 on 2007-07-07
i think youll find it actually just wants YOUR password NOT the root password.

---

