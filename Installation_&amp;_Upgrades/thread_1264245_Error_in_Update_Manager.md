---
title: "Error in Update Manager"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by gordong11 on 2009-09-12
Hi , all.

BTW this is my first Ubuntu install in a few years, I"m in love, so I'm somewhat of a noob.

I'm getting this error when I run the update manager(9.04). Can anyone help me solve this issue?
Attached is the screenshot. Thanks

---

### Post by gordong11 on 2009-09-12
Solved on my own via terminal enties below: 

1. gpg --keyserver subkeys.pgp.net --recv 6AF0E1940624A220


2. gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -   (both on same entry line, only got message "OK")

3. sudo apt-get update


I hope I did the right thing, I no longer get the error, but I hate doing stuff I know little about.

---

