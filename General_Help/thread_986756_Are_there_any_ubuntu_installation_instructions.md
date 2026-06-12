---
title: "Are there any ubuntu installation instructions"
date: 2008-11-18
forum: General Help
---

### Post by hill0093 on 2008-11-18
md5sum verified the check value.
The burned CD had “no errors found”.
ubuntu-linux-i386.iso installed and went thru the “restart now”
The update manager found 34 updates and installed them.
Are there any general reasonably comprehensive installation 
instructions somewhere so I can get 8.10 to work?
I need 
-the right sized screen recognized
-DVDs to play and retrieve data
-openoffice writer to print
-Sun java-6 jdk to work and print

---

### Post by plucky on 2008-11-19
Welcome to Ubuntu.

Click on the Psychocats Website Link in my signature.This website has good information about using Ubuntu and how to do many things.


> the right sized screen recognized

Open a terminal window **Applications > Accessories > Terminal** and post output of command ```
lshw -C video
``` so we can see what video hardware you have.

> DVDs to play and retrieve data

See the information for adding the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu) and what to install to allow DVD's to play on Ubuntu.


> openoffice writer to print


Have you installed your printer?
What printer do you have?

> Sun java-6 jdk to work and print 

Install **Ubuntu-restricted-extras** either from Add/Remove or from a terminal with ```
sudo apt-get install ubuntu-restricted-extras
```


Good Luck & enjoy :)

---

### Post by oldos2er on 2008-11-19
In addition to the psychocats.net website, there is [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by dabl on 2008-11-19
and

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

