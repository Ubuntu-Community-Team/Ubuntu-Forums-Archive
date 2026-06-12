---
title: "upgrdae psql to 8.4"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by dimkof on 2009-08-04
I have Ubuntu 8 installed.  I want to upgrade psql from 8.3.7 to latest 8.4.  psql page states: "[Ubuntu]("http://www.ubuntu.com/") users may install PostgreSQL using the apt utility."

but when i try, i get: 

sudo apt-get install postgresql
Reading package lists... Done
Building dependency tree
Reading state information... Done
postgresql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

So how do i get the OS to know it needs an upgrade to 8.4 for psql?

---

### Post by Partyboi2 on 2009-08-05
Hi, you can add the 3rd party repo from [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/%7Epitti/+archive/postgresql") and install it. If you are unsure on how to add the repo post back and someone should be able to help you.

---

### Post by dimkof on 2009-08-05
Thanks!  Although that link describes how to upgrade, it does it assuming the full gui is enabled.  I am using a bare bones ubuntu8 so was hoping to get help with how to do it through an ssh session - command line.  So if anyone can help with that - that would be great.  if not - thanks for the link it gives me more information and a push in the right direction.

---

### Post by Partyboi2 on 2009-08-05
Login to your computer with [[COLOR=Blue]Ssh[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo"), once you are connected add the repos to your sources.list 
```
echo deb [http://ppa.launchpad.net/pitti/postgresql/ubuntu](http://ppa.launchpad.net/pitti/postgresql/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list
```
```
echo deb-src [http://ppa.launchpad.net/pitti/postgresql/ubuntu](http://ppa.launchpad.net/pitti/postgresql/ubuntu) hardy main| sudo tee -a /etc/apt/sources.list
```
then
add the key

```
gpg --keyserver keyserver.ubuntu.com --recv 8683D8A2
gpg --export --armor 8683D8A2 | sudo apt-key add -
```

then ```
sudo apt-get update
sudo apt-get upgrade
``` This should upgrade to the later version of postgresql

---

