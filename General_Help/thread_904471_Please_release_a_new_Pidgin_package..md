---
title: "Please release a new Pidgin package."
date: 2008-08-29
forum: General Help
---

### Post by NoobieDoobieDo on 2008-08-29
The latest version of Pidgin is 2.5 [August 24, 2008] yet the release for Ubuntu is 2.4.1

This version has some sort of bug which makes it so it nearly constantly says "Available - Waiting for network connection" even though I'm :

-online
-connected
-chatting
-can see everyone on my buddy list

I :

-do not have a router
-do not use a switch
-have had this problem repeatedly
-do not have trouble w/any other network apps

I just experienced a bug with AIM where I sent someone several messages and they received none.  I am NOT interested in compiling from source NOT because I CANT but because I don't desire to have to manually update everything.

Please resolve this without delay as we ALL rely on yall to keep the packages up to date.

---

### Post by Bliepo32 on 2008-08-29
You install the latest version from source. Download it from [http://pidgin.im/download/source/]("http://pidgin.im/download/source/"). Then, unpack it, and do the following:
```

sudo apt-get install build-essential
cd [path to pidgin folder]
./configure
make
sudo make install

```

---

### Post by Tom--d on 2008-08-29
No need!

Just download the packages from [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) and download them all.

Install the pidgin-data first. Then libpurple0 and lastly pidgin.

**Remove the old Pidgin before installing the new one!**

---

### Post by Joeb454 on 2008-08-29
The repositories only get updated with each Ubuntu release. Unless you want to compile it yourself, or check hardy-backports for the package, you will have to wait.

Other distro's are "rolling-release" such as Arch, which means the repo's are updated quite frequently

---

### Post by tuxxy on 2008-08-29
Use [GetDeb]("http://www.getdeb.net/") for any updated packages

---

### Post by NoobieDoobieDo on 2008-08-29
> **tuxxy said:**
> Use [GetDeb]("http://www.getdeb.net/") for any updated packages

Thank you.

---

### Post by tuxxy on 2008-08-29
No Problem, you can mark the thread solved now too :)

---

