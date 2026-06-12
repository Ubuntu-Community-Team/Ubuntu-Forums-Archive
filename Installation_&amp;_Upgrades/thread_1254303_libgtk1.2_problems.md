---
title: "libgtk1.2 problems"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by manikmalhotra on 2009-08-31
hall9@hall9-desktop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2

I am a new user to ubuntu.I had the follwing error message when trying to install this package for WINE.Please help.

---

### Post by wojox on 2009-08-31
Open Sytem > Administration > Synaptic Package Manager and search libgtk

---

### Post by Partyboi2 on 2009-08-31
Hi. make sure you have the "universe" repo enable in Software Sources (System>Admin>Software Sources) under the first tab.

---

### Post by manikmalhotra on 2009-08-31
universe -enabled & i have libgtk in synaptics but its not libgtk 1.2 
Any other suggestions??

---

### Post by wojox on 2009-08-31
Are you using 9.04 Jaunty? I have it in mine.

---

### Post by Partyboi2 on 2009-08-31
What version of Ubuntu are you using?

---

### Post by manikmalhotra on 2009-09-03
version of my ubuntu is 9.04

---

### Post by Partyboi2 on 2009-09-03
Can you open a terminal and post your sources.list please
```
cat /etc/apt/sources.list
```

---

### Post by bratliff on 2010-05-19
libgtk1.2 is not in the Ubuntu 10.04 repositories.
Where do I find it?
bob


> **wojox said:**
> Open Sytem > Administration > Synaptic Package Manager and search libgtk

---

### Post by bsspeters on 2010-05-27
> **bratliff said:**
> libgtk1.2 is not in the Ubuntu 10.04 repositories.
Where do I find it?
bob

I had to search around a while for the package. 

Install packages in order:

1: [http://packages.ubuntu.com/dapper/all/libgtk1.2-common/download](http://packages.ubuntu.com/dapper/all/libgtk1.2-common/download) + [http://packages.ubuntu.com/dapper/libglib1.2](http://packages.ubuntu.com/dapper/libglib1.2) ( choose your system )
2: Finally for libgtk1.2 : [http://packages.ubuntu.com/dapper/libgtk1.2](http://packages.ubuntu.com/dapper/libgtk1.2) (choose your system)

For Ubuntu 10.4 you can just run through the Gdebi package installer

Then just use the "linux32 sh et-linux-2.55.x86.run" command in your terminal and you should be all set!

---

