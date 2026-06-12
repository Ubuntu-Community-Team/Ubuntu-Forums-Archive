---
title: "how do i install kexi??help!!"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by luca_blight13 on 2009-03-13
hello there... im new with ubuntu and it seems that its much harder to install softwares in linux. i have a problem installing kexi, ive downloaded a .tar file and putted it in my desktop... when i extract it, its just a folder with lots of files inside... how am i gonna install this one?  ive typed ./config and prints out details... which is i can't understand since im a beginner and willing to learn linux... then when i have typed 'make'... its prints out this

make: *** No targets specified and no makefile found.  Stop.

what should i do? what is the correct way of installing softwares in linux? help!!!

---

### Post by zvacet on 2009-03-13
You probably have **install file** in that folder.Read it and look for **read me** file,because that can also be helpful.To be sure that you have all dependencies before you are going to compile type in terminal(but be in directory where you downloaded package;Desktop in your case)

```
sudo apt-get build-dep package_name
```

**package_name**= name of package you are trying to compile

In most cases it is 3 steps process

1. configure
2.make
3.sudo make install

---

### Post by zvacet on 2009-03-13
You have kexi in the repos.Just be sure that you have universe repo enabled in **system>admin>software sources**.If you have it wnabled go to the synaptic and in search box type kexi and when you find it mark it for install.

---

### Post by khelben1979 on 2009-03-13
Or you can try:
```
sudo apt-get install kexi
```

---

### Post by luca_blight13 on 2009-03-15
tnx guys ill gonna try this

---

