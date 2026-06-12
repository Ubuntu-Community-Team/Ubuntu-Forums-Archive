---
title: "How to install rpms?"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by mlinuxuser on 2009-10-07
How to install rpm softwares in ubuntu 9.04?

---

### Post by howefield on 2009-10-07
> **mlinuxuser said:**
> How to install rpm softwares in ubuntu 9.04?

You can't.

You can however convert them to .deb with Alien, but how good this is, I couldn't vouch.

You can install Alien using Synaptic Package Manager.

---

### Post by Mark Phelps on 2009-10-07
My personal experience using converted rpms is mixed -- some worked, some didn't.  

Apparently, some of the libraries and entries are different such that, even after a conversion of an .rpm file to a .deb file, it doesn't really have all the correct entries.

So, it's generally not a good idea to try to force installation of converted .rpm files in Ubuntu.

---

### Post by mlinuxuser on 2009-10-07
thanks for the suggestions. I wan to know that whether alien is a command line utility?

---

### Post by wojox on 2009-10-07
Yes you need the terminal: [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by inobe on 2009-10-07
> **mlinuxuser said:**
> How to install rpm softwares in ubuntu 9.04?

you can avoid that !


what's the application ?

---

### Post by mlinuxuser on 2009-10-08
MySQL

---

### Post by doas777 on 2009-10-08
looks like it is already in the repos:
[http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/)

---

