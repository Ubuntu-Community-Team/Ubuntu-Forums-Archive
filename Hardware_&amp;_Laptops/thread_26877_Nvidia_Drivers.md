---
title: "Nvidia Drivers"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by rosagonzpe on 2005-04-14
I am trying to optimize my nvida card, to have better dvd support, 3d etc ...

*  When i try "apt-get install nvidia-glx" the system answers backs that the package is not available.

*  My sources.list

----------------------------------

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
 
# DVDCSS/xvid/other legally questionable packages
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
 
# Backports
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe
 
# MPlayer
deb [http://sh.nu/~crimsun/](http://sh.nu/~crimsun/) ./

Thanks on advance !!

---

### Post by heimo on 2005-04-14
nvidia-glx is in restricted
 
These to sources.list
```
 
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary restricted

``` 
 
And then you can install
```
 
sudo apt-get update
sudo apt-get install nvidia-glx

```
 
EDIT: typo

---

### Post by rosagonzpe on 2005-04-14
Thank you very much, ubuntu people is awesome !!
Thanks mate

---

