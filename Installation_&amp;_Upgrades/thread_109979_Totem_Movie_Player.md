---
title: "Totem Movie Player"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by rjay3 on 2005-12-29
Totem Movie Player does not play DVD's. Is there something I need to know to make it to play plain ol' dvd movies? Thanks.

---

### Post by qamelian on 2005-12-29
Have you install libdvdcss2? Without it installed Totem won't be able to decrypt the content scrambling system used on most DVDs. You can get it from the PLF Ubuntu repositories by adding the following lines to /etc/apt/sources.list.
> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
Then from a terminal, enter the following:
> sudo apt-get update
sudo apt-get install libdvdcss2

---

### Post by kingsidy on 2006-01-02
1. install libdvdcss2
2. install totem-xine > sudo apt-get install totem-xine or install vlc. the default totem install is based on gstreamer which is not that good when it comes to dvds. so switch to the xine backend.

---

### Post by rjay3 on 2006-01-02
Thank you for all the replies, followed your advise and it's now working!!:D :D

---

### Post by rjay3 on 2006-01-02
I thought everything was going well until I tried to play a home DVD but got an error message about no plugin to handle the movie? I attached the png error cause I couldn't figure out how to insert the image. Thanks.

---

