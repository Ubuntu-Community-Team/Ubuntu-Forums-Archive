---
title: "Gutsy~how get winxp to run on with ubuntu??"
date: 2008-11-25
forum: General Help
---

### Post by KEE on 2008-11-25
here look [http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0) thats what i mean btw. and how do you do this? please help!!

---

### Post by damis648 on 2008-11-25
You must virtualize Windows in order to do this. I use Virtualbox it works quite well. To check it out, try
```
sudo apt-get install virtualbox-ose
```
, but note you will have to install Windows in the VM and configure and all, etc.

---

### Post by KEE on 2008-11-25
> **damis648 said:**
> You must virtualize Windows in order to do this. I use Virtualbox it works quite well. To check it out, try
```
sudo apt-get install virtualbox-ose
```
, but note you will have to install Windows in the VM and configure and all, etc.

is there a link to know how its done?

---

### Post by damis648 on 2008-11-25
After installing virtualbox, Just start it with Applications>System Tools>Sun Virtualbox. Create a new VM and follow the prompt on screen. For the cube, do
```
sudo apt-get install compizconfig-settings-manager
```
and then go to System>Preferences>CompizConfig settings Manager and enable the cube.

---

### Post by KEE on 2008-11-25
> **damis648 said:**
> After installing virtualbox, Just start it with Applications>System Tools>Sun Virtualbox. Create a new VM and follow the prompt on screen. For the cube, do
```
sudo apt-get install compizconfig-settings-manager
```
and then go to System>Preferences>CompizConfig settings Manager and enable the cube.k

---

### Post by bodhi.zazen on 2008-11-25
There are how-tos on how to do this in the Virtualization section, see the mega thread.

Also, compiz is in the repositories so you should not be needing to install anything from source (tar balls).

---

