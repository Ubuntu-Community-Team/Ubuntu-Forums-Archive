---
title: "uuencode: command not found"
date: 2008-09-26
forum: General Help
---

### Post by abasel on 2008-09-26
I have a script which when I run, generates the following error:


./generate_ga_passwords.sh: line 16: uuencode: command not found

Line 16 is 
str=`head -c 5 /dev/random | uuencode -m - | tail -n 2 | head -n 1`

When I try and install uuencoce, I get the following:

root@Google-Apps:~# apt-get install uuencode
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package uuencode is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package uuencode has no installation candidate

How do I fix this?

---

### Post by Sycron on 2008-09-26
Search here the package: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by tacutu on 2008-09-26
install sharutils

---

### Post by abasel on 2008-09-26
I've found sharuitls; [http://packages.ubuntu.com/source/hardy/sharutils]("http://packages.ubuntu.com/source/hardy/sharutils") (there doesn't seem to be an apt-get install option for it.

How do I install these files and do I need to download all three?

---

### Post by Sycron on 2008-09-28
Put them in a folder, for example on folder **jiji** which is on the **desktop** , open a terminal and type:
```
cd D*/jiji && sudo dpkg -i *.deb
```

---

### Post by tacutu on 2008-09-28
sudo apt-get install sharutils
works juuust fine.

---

