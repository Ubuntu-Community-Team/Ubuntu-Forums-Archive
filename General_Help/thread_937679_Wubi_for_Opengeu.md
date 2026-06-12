---
title: "Wubi for Opengeu?"
date: 2008-10-04
forum: General Help
---

### Post by Gilean on 2008-10-04
Hi guys, i was wondering if is it possible to make Wubi working with opengeu?

---

### Post by Gilean on 2008-10-05
up.

---

### Post by ago on 2008-10-06
Gilean, assuming that Opengeu comes with a Live CD, yes, but wubi will need to be recompiled after adding a section to isolist.ini.

---

### Post by Gilean on 2008-10-07
Ago is there any how to?

ITA: Ago c'e' qualche guida per farlo? ?vorrei provare opengeu con la sicurezza che solo wubi mi ha dato sin'ora,grazie mille :)

p.s. dove trovo i sorgenti di wubi?

---

### Post by ago on 2008-10-07
If it's for end users I do not think that modifying wubi is worth the trouble.
You can achieve the same effect by installing any Ubuntu using Wubi, then before rebooting, swap c:\ubuntu\install\*buntu*.iso with the ISO you actually want to use. You might also have to edit c:\ubuntu\install\custom-installation\preseed.cfg and in particular replace "ubuntu-desktop" with whatever desktop package is appropriate for your distro. This assumes that the ISO uses Ubiquity.

An even more convenient way to try Ubuntu compatible distros, is to install Ubuntu, then add any distro specific repository, then install the appropriate desktop package.

---

### Post by Gilean on 2008-10-07
tnx ago. in my pc i already have ubuntu installed via wubi...is possible to install another wubi with opengeu, or i must uninstall ubuntu first?

---

### Post by ago on 2008-10-07
> **Gilean said:**
> tnx ago. in my pc i already have ubuntu installed via wubi...is possible to install another wubi with opengeu, or i must uninstall ubuntu first?

There should be no need to uninstall ubuntu, most likely opengeu provides a repository and a (meta) package that can be installed on top of ubuntu, such as "opengeu-desktop" (just a guess).

---

### Post by Gilean on 2008-10-08
> **ago said:**
> If it's for end users I do not think that modifying wubi is worth the trouble.
You can achieve the same effect by installing any Ubuntu using Wubi, then before rebooting, swap c:\ubuntu\install\*buntu*.iso with the ISO you actually want to use. You might also have to edit c:\ubuntu\install\custom-installation\preseed.cfg and in particular replace "ubuntu-desktop" with whatever desktop package is appropriate for your distro. This assumes that the ISO uses Ubiquity.

An even more convenient way to try Ubuntu compatible distros, is to install Ubuntu, then add any distro specific repository, then install the appropriate desktop package.

Ago sorry, in the preseed.cfg for installing opengeu, what must i write instead of ubuntu-desltop exactly? bye and tnx for your help

---

### Post by ago on 2008-10-08
> **Gilean said:**
> Ago sorry, in the preseed.cfg for installing opengeu, what must i write instead of ubuntu-desltop exactly? bye and tnx for your help

There must be an equivalent meta package to ubuntu-desktop, you should ask in the opengeu mailing list/chat

---

### Post by Gilean on 2008-10-08
Ago, opengeu is derivated from Ubuntu. I noticed that this distro has wubi in the iso, but after installing wubi, i reset pc, the logo starts and then..a cross cursor and black screen (i'm able to move the cursors)...do u know hot to start it?

here is the site

[http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

---

### Post by ago on 2008-10-08
Puoi installare "sopra" Ubuntu: [http://opengeuwiki-en.intilinux.com/index.php?title=How_to_install_OpenGEU_8.04.1_from_packages](http://opengeuwiki-en.intilinux.com/index.php?title=How_to_install_OpenGEU_8.04.1_from_packages)

---

