---
title: "ATI installation won't finish"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by withpz on 2006-03-12
I have been trying to install my ATI on my laptop many times but always there are some problems with it. i am pretty much new to linux. i have downloaded the ATI installer and the drivers and after I write in terminal "sh ati-driver-installer-8.19.10-i386.run" the installation begins but shortly there is a message that stops it. the message is "YOU NEED TO RUN THIS INSTALLER AS A SUPER-USER". i do not know where to login to super-user account...

---

### Post by 4dz0 on 2006-03-12
You simply need to use the sudo command, this will give you root privileges, so for example

sudo sh ati-driver-installer-8.19.10-i386.run

you will then be prompted for a password, this password should be the same as your usual login password.

---

### Post by withpz on 2006-03-12
thank you. it helped:)

---

