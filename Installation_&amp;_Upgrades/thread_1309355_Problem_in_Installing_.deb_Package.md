---
title: "Problem in Installing *.deb Package"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by cybercrawler on 2009-11-01
Hi fellaz!

          I am trying to install a G++ compiler in my ubuntu 9.04 (2.6.28-11). Its real easy that a kid can use synaptico and other GUI to install it in a linux box. But i am trying to install it manually via the terminal.

I have used the "dpkg -i *.deb" command in the directory where the package is located, its giving me some error messages, and when tried to install the same package by double clicking on the package, it gives me an error stating that "Broken Package" Is there any thing else that i can do to install the *.deb package manually in my linux box.

I dont wanna use an online download managers. My box is not hooked into the internet.

Thanx for your help in advance.....


Awaiting for your replies.....

---

### Post by albandy on 2009-11-01
sudo apt-get install g++
read the requierd packages.
say N to not install through internet

download each package in a folder
then enter de folder and type
sudo dpkg -i *.deb

---

