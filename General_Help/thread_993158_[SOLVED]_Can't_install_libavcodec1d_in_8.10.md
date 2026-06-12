---
title: "[SOLVED] Can't install libavcodec1d in 8.10"
date: 2008-11-25
forum: General Help
---

### Post by rbjscv on 2008-11-25
I trying to install libavcodec1d in 8.10 but am unable to do so.  It's needed for the program avi-ogminfo.

Any help?

---

### Post by rbjscv on 2008-11-25
Found my own fix here:

[http://packages.ubuntu.com/gutsy/libs/libavcodec1d](http://packages.ubuntu.com/gutsy/libs/libavcodec1d)

and then just began working my way back satisfying the needed dependencies until: BINGO!  app installed and works just like it did in Hardy.

---

### Post by ashmew2 on 2008-12-10
Hey..I had the same issues ( I wanted to insall dvdstyler's wx libraries)..Anyways , I just added this line to my /etc/apt/sources.list :

```
deb http://security.ubuntu.com/ubuntu gutsy-security main 
```

Did a 
```
sudo apt-get update
```

And then a
```
sudo apt-get install libavcodec1d
```

It installed! Thanks for the link though! :D

---

### Post by snebtor on 2009-02-26
Totally helpful :KS:KS:KS:KS:KS:KS

---

