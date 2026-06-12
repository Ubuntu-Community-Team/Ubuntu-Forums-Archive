---
title: "booting from floppy"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by craigsman on 2005-12-14
Hello,
How do I set up a bootalbe floppy disk. My computer is sooo old that it doesn't boot from a CD so I need to boot from floppy which can then trigger an installation.
Thanks

---

### Post by NotJustANewbie on 2005-12-17
[http://www.bootdisk.com/](http://www.bootdisk.com/)

Google is your good friend ;)

---

### Post by ricky2k1 on 2005-12-17
can i use a debian boot disk and then install from CD?
if yes, please tell me how

thanks

---

### Post by afhp on 2005-12-17
Mentioned here [http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843) and here
[http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3](http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3)

---

### Post by Liquibyte on 2005-12-18
Well done to all involved, very well done indeed. I was able to get this up and running quite easily once I got my brain out of the way.

First, I went and ditched my testing install floppies and got these: > [http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/)
 [http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/)
 [http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://archive.progeny.com/debian/dists/sarge/main/installer-i386/current/images/floppy/)

I assume any mirror would do, but these were the first ones I came upon with help from here.

Second, install debian with only the most base system (i.e. When it asks you if you want a desktop, internet server, choose packages etc., uncheck everything).

Third, edit your /etc/apt/sources.list like so:

```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://archive.ubuntu.com/ubuntu breezy main universe restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
```

You can comment out or even leave out altogether the deb-src lines if you don't plan on doing any developing, 'tis up to you, I'm a programmer by mental illness.

Fourth, do an 'apt-get update'

Fifth, do an 'apt-get dist-upgrade'

Sixth, do an 'apt-get install ubuntu-base ubuntu-desktop' (You can also do 'kubuntu-desktop' if you're so inclined, I did).

Seventh, and this bit is up to you: You might consider changing your kernel version from aptitude before rebooting and/or installing more stuff. You can always do it later I suppose, but I've gotten used to using aptitude in debian over the last couple of weeks.

I must say that I'm mighty impressed with the work that has gone into this distro. I may just have to get involved now.

---

