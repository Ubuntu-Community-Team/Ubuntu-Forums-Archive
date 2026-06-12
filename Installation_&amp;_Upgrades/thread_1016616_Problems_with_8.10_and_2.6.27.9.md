---
title: "Problems with 8.10 and 2.6.27.9"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by tomleyton on 2008-12-20
Hey,

I have ubuntu 8.10 installed and a recently updated kernel 2.6.27.9, for some reason when it's loading I see the ubuntu logo and the progress bar, but afterwards it's like theres no more signal to the monitor and everything goes blank leaving my monitor with a ? box floating on it.

Has anyone else experienced this problem? When I go back to one of the previous kernels it's fine...

Thanks,
Tom

---

### Post by Pumalite on 2008-12-20
Go into Recovery Mode and do this:
apt-get -f install
apt-get update
apt-get dist-upgrade

---

### Post by Pumalite on 2008-12-20
When you get to the menu; choose 'Drop to a Shell'

---

