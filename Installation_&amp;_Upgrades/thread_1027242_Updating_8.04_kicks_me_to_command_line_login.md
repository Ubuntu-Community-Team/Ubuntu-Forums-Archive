---
title: "Updating 8.04 kicks me to command line login"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by margazhang on 2009-01-01
Each time when I see the prompt for updates, I download all to keep my 8.04 install on one computer updated. 

But now I have a problem after updating to kernel 2.6.24-22, I cannot get to the familiar graphic login screen. It only gives a dark background command line login. After login everything is command line. 

What is the problem - how can I fix that?

I would like to UPGRADE to 8.10 as I like it a lot after fresh installing it on another newer computer. [This link]("http://www.ubuntu.com/getubuntu/upgrading") shows ways to upgrade in the graphic mode. But how can I upgrade to 8.10 from the command line? I want to save the data you know.

---

### Post by margazhang on 2009-01-01
Anyone who has the same problem? Anyone can help?

---

### Post by Bluebell392 on 2009-01-01
Updating from the command-line is simple. Getting your graphical environment is also simple. First, to upgrade: run these three commands: sudo apt-get update sudo apt-get upgrade sudo apt-get dist-upgrade. To get the graphical environment, try this: type sudo init 1, then at the menu that appears, choose xfix.

---

