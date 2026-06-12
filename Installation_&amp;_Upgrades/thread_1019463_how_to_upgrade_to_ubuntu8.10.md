---
title: "how to upgrade to ubuntu8.10"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by arunkumar413 on 2008-12-23
I am using Ubuntu 8.04 on system.Today i received Ubuntu 8.10 CD.I want to upgrade to 8.10.Help me how to upgrade

---

### Post by neu2buntu on 2008-12-23
think this may work....firstly make sure your system is up to date 
```
sudo apt-get update
```then place your cd in tray 

goto >system>administration>software sources....hopefully the cd shows up here and tick it

then run the sudo apt-get update again , if my memory serves me right you should be able to upgrade from here,while keeping all your settings intact


you can also update from >system>administration>updatemanager

---

### Post by namdung on 2008-12-23
> **arunkumar413 said:**
> I am using Ubuntu 8.04 on system.Today i received Ubuntu 8.10 CD.I want to upgrade to 8.10.Help me how to upgrade

I suggest you to reconsider upgrading to Intrepid. Hardy is a LTS which is a much stable version. The other versions may have more features but is most likely to have more bugs. 8.04.2 is coming out in Jan.

You might wanna try out Intrepid first in virtualization using virtualbox etc before the final upgrade.


Good luck!!!

---

### Post by arunkumar413 on 2008-12-23
> **chrissy.mc.1@hotmail.co.u said:**
> think this may work....firstly make sure your system is up to date 
```
sudo apt-get update
```

then place your cd in tray 

goto >system>administration>software sources....hopefully the cd shows up here and tick it

then run the sudo apt-get update again , if my memory serves me right you should be able to upgrade from here,while keeping all your settings intact

There are some softwares installed on my system which i downloaded from internet.Now if i upgrade,will i have to install them again.

---

### Post by neu2buntu on 2008-12-23
no they will still be there.....   and heres a good link for you,just noticed and also you have to click on >system>administration>softwaresources>updates and make sure you choose normal releases....its in this link

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by arunkumar413 on 2008-12-23
> **chrissy.mc.1@hotmail.co.u said:**
> no they will still be there.....   and heres a good link for you,just noticed and also you have to click on >system>administration>softwaresources>updates and make sure you choose normal releases....its in this link

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
many thanks for helping me.

---

### Post by neu2buntu on 2008-12-23
let m,e know how you get on (i see it mentioning an ALTERNATE cd hope the normal 8.10 cd works this way)......      and anytime you thank someone on a post click the yellow/red icon beside quote hint hint

---

### Post by surj08 on 2008-12-23
> **arunkumar413 said:**
> I am using Ubuntu 8.04 on system.Today i received Ubuntu 8.10 CD.I want to upgrade to 8.10.Help me how to upgrade

alt+f2 put in "update-manager -d" without the quotes

---

### Post by arunkumar413 on 2008-12-23
> **surj08 said:**
> alt+f2 put in "update-manager -d" without the quotes
does the 8.10 CD contain softwares or else i have to download from internet?

---

