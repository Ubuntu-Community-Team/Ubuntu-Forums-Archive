---
title: "A Good sources.list?"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Octane on 2005-06-19
Hi all, I'm running Kubuntu 5.04

Here is my sources.list
```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

# Marillat
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb http://cyberspace.ucla.edu/marillat unstable main

# libfasttrack-gift
# deb ftp://ftp.berlios.de/pub/gift-fasttrack unstable main
deb-src ftp://ftp.berlios.de/pub/gift-fasttrack unstable main

deb ftp://ftp.tux.org/pub/java/debian sarge non-free

#wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

Here are the results when I apt-get update
```
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://wine.sourceforge.net binary/ Release.gpg
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://archive.ubuntu.com hoary-updates Release.gpg [189B]
Ign http://cyberspace.ucla.edu unstable Release.gpg
Hit ftp://ftp.tux.org sarge Release.gpg
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Get:4 ftp://ftp.tux.org sarge Release [750B]
Ign http://cyberspace.ucla.edu unstable Release
Hit http://archive.ubuntu.com hoary-updates Release
Ign http://wine.sourceforge.net source/ Release.gpg
Hit http://cyberspace.ucla.edu unstable/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Hit http://wine.sourceforge.net binary/ Release
Hit ftp://ftp.nerim.net unstable Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit ftp://ftp.nerim.net unstable Release
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://wine.sourceforge.net source/ Release
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Ign http://wine.sourceforge.net binary/ Packages
Ign http://wine.sourceforge.net source/ Sources
Hit http://security.ubuntu.com hoary-security/main Packages
Get:5 ftp://ftp.tux.org sarge/non-free Packages
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Ign ftp://ftp.tux.org sarge/non-free Packages
Hit http://wine.sourceforge.net binary/ Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit ftp://ftp.tux.org sarge/non-free Packages
Hit http://security.ubuntu.com hoary-security/multiverse Packages
Hit ftp://ftp.nerim.net unstable/main Packages
Hit http://archive.ubuntu.com hoary-updates/main Packages
Hit http://archive.ubuntu.com hoary-updates/restricted Packages
Hit http://archive.ubuntu.com hoary-updates/universe Packages
Hit http://archive.ubuntu.com hoary-updates/multiverse Packages
Hit http://wine.sourceforge.net source/ Sources
Get:6 ftp://ftp.berlios.de unstable Release.gpg
Ign ftp://ftp.berlios.de unstable Release.gpg
Get:7 ftp://ftp.berlios.de unstable Release
Ign ftp://ftp.berlios.de unstable Release
Get:8 ftp://ftp.berlios.de unstable/main Sources
Ign ftp://ftp.berlios.de unstable/main Sources
Hit ftp://ftp.berlios.de unstable/main Sources
Fetched 753B in 60s (12B/s)
Reading package lists... Done
```
Lots of errors. I was wondering if anyone has a nice sources.list with the most diverse list of repos that are also reliable?

---

### Post by bored2k on 2005-06-19
I don't really see the errors you're talking about..
Anyway, here is mine:
>  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multive rse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse  restricted


---

### Post by XDevHald on 2005-06-19
Octane, do you have the gpg key or a link where I can get this for the  >  deb [ftp://ftp.tux.org/pub/java/debian](ftp://ftp.tux.org/pub/java/debian) sarge non-free 

---

### Post by Octane on 2005-06-19
[QUOTE=bored2k]I don't really see the errors you're talking about.[/QUOTE]
Ignores aren't errors?  :-#  ](*,)

---

### Post by Octane on 2005-06-19
[QUOTE=BB]Octane, do you have the gpg key or a link where I can get this for the[/QUOTE]
I can't seem to find where I got it. Is there a way I can output it so I can let you have it?

---

### Post by TravisNewman on 2005-06-19
yeah none of those are errors. That's standard output.

---

### Post by Octane on 2005-06-19
[QUOTE=panickedthumb]yeah none of those are errors. That's standard output.[/QUOTE]
reat im an asshat

---

### Post by bored2k on 2005-06-19
[QUOTE=Octane]reat im an asshat[/QUOTE]
 And error would not allow to downloading anything through apt.

---

### Post by XDevHald on 2005-06-20
[QUOTE=Octane]I can't seem to find where I got it. Is there a way I can output it so I can let you have it?[/QUOTE]
 Goto your Update Manager in System > Administration > Ubuntu Update Manager and click on "Preferences" below, then "Authentication" and it will give you the listed keys.

The key I am needing is **BB5E459A529B8BDA**

---

### Post by Octane on 2005-06-20
[QUOTE=BB]Goto your Update Manager in System > Administration > Ubuntu Update Manager and click on "Preferences" below, then "Authentication" and it will give you the listed keys.

The key I am needing is **BB5E459A529B8BDA**[/QUOTE]
using Kubuntu here

---

### Post by XDevHald on 2005-06-20
[QUOTE=Octane]using Kubuntu here[/QUOTE]
It shows hoary in your sources. Not sure if it matters if it's Kubuntu or not when it's hoary packaging. Can someone follow up on this?

---

### Post by Octane on 2005-06-20
Damn. I could have *sworn* I placed this thread in a Kubuntu forum. I'm sorry. 
[QUOTE=BB]It shows hoary in your sources. Not sure if it matters if it's Kubuntu or not when it's hoary packaging. Can someone follow up on this?[/QUOTE]
No, hoary is just fine -- see KUDOS Kubuntu FAQ for verification: [http://kudos.berlios.de/kf/kf1.html#h2add](http://kudos.berlios.de/kf/kf1.html#h2add)

---

### Post by XDevHald on 2005-06-20
[QUOTE=Octane]Damn. I could have *sworn* I placed this thread in a Kubuntu forum. I'm sorry. 

No, hoary is just fine -- see KUDOS Kubuntu FAQ for verification: [http://kudos.berlios.de/kf/kf1.html#h2add](http://kudos.berlios.de/kf/kf1.html#h2add)[/QUOTE]
 Thanks Octane, good point out :D

---

### Post by XDevHald on 2005-06-20
Octane, the key can be obtained by doing the following commands in terminal.

 >  ~$ sudo -i
~# echo "deb ${MIRROR}/debian sarge non-free" >> /etc/apt/sources.list
~# gpg --keyserver wwwkeys.pgp.net --recv-keys 0x529B8BDA
~# gpg --armor --export 0x529B8BDA | apt-key add - 

Thanks for the link, helped out a lot :D

---

