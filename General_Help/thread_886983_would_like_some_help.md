---
title: "would like some help"
date: 2008-08-11
forum: General Help
---

### Post by zaptear on 2008-08-11
i'm trying to add 
   deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main

 references to my repository list
but when i type in  /etc/apt/sources.list 
i get  Permission denied can i get some help on this?

---

### Post by sisco311 on 2008-08-11
Type
```
gksu gedit /etc/apt/sources.list
```to edit the file, as root, with the default text editor(gedit).

---

### Post by zaptear on 2008-08-11
thanks that got me in i just can't seem to get this program to run but i will work on it till i do

---

### Post by zaptear on 2008-08-11
Repository

If you have a Debian based system (such as Ubuntu) then you can install pre-built vesrions of the launcher

There are two versions of the launcher available, lotrolinux is the base version while lotrolinux-gecko uses the gecko/mozilla web browser.

For Ubuntu Hardy systems add the following references to your repository list:

   deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main

If you have Ubuntu Dapper or Debian Etch add:

   deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) dapper main

If you have any other Debian system try one of the above, more distributions may be added in the future.

ok i'm not doing something right here so i just add the lines in my gksu gedit /etc/apt/sources.list or am i missing something im trying to install  lotrolinux and i'm just not understanding ware i need to input this so it installs

---

### Post by zaptear on 2008-08-11
still trying to do this anyout have a link i cud go to try read up on this?

---

### Post by x1a4 on 2008-08-11
Hi,
Add the text 
```
deb http://ppa.launchpad.net/ajackson-bcs/ubuntu hardy main
```
to the file /etc/apt/sources.list using 'gksudo gedit' like sisco311 said, then update your lists of packages.  From the command line:
```
sudo apt-get update
```
or just click the 'Reload' button in Synaptic.

Now your system is aware of the app you want allowing you to install it.

---

### Post by zaptear on 2008-08-11
oh ok thanks so much for the help sorry for being so nooby about

---

### Post by x1a4 on 2008-08-11
No problem.  That's what these forums are for--to help.

---

