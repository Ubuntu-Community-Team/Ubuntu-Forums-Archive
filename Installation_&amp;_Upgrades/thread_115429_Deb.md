---
title: "Deb"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by timmeh72110 on 2006-01-10
Could not open "amarok_1.3.1-0ubuntu4_i386.deb"

Archive type not supported.

I'm new to linux(Obivously)  how do I fix this? Err I don't know nothing about this debian system I've only used SUSE but ubuntu looks very very promising please help
Thank you in advance


Windows is crap

---

### Post by ruben_b on 2006-01-10
do you want to install this deb file?

if so, use the following method:

-open a terminal
-change to the directory where you stored the file
-type:
sudo dpkg -i amarok_1.3.1-0ubuntu4_i386.deb


edit:
by the way, amarok 1.3.1 is allready available via synaptic.
-so just open synaptic (system->systemtools->synaptic)
-click update
-click the search button
-search for amarok
-right click on amarok an select install
-proceed

---

### Post by timmeh72110 on 2006-01-10
enlighten me on how to change directories

---

### Post by Jimmey on 2006-01-10
```
cd /directory/name
```
Example - 
```
cd /home/james/programming
```

---

### Post by timmeh72110 on 2006-01-10
timmeh@ubuntu:~$ cd /home/timmeh/Desktop
timmeh@ubuntu:~/Desktop$ sudo dpkg -i amarok_1.3.1-0ubuntu4_i386.deb
Password:

Alright it wont let me type the password what is wrong with this?


Thanks again

---

### Post by christhemonkey on 2006-01-10
When you type the password in, it does not move the cursor so just trust in it and type your password :)

---

### Post by timmeh72110 on 2006-01-10
But it doesn't show up? so what do I do to make it go in?

---

### Post by Zahrber on 2006-01-10
do you actually know the password..if so then just type the password in correctly and hit enter then the package will be installed.

If you have dependencies you need then try the sudo dpkg -f ***.deb

---

