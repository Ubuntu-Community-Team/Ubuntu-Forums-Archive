---
title: "aptitude repository?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2009-05-09
My Kubuntu 9.04 amd64 DVD did not install kppp, so I am trying to install wvdial just for the purpose of connecting via my 56K phone modem, which is all I have to reach the Net with. I downloaded (using another computer) and transferred to my amd64 machine the following amd64 binary packages:

wvdial 1.6
libuniconf 4.4
libwvstreams 4.4 base
libwvstreams 4.4 extras
libxplc 0.3.13

These packages are sitting in a directory /home/david/sw/wvdial

I want to install them with Aptitude. I don't want to invoke the apt-get command directly. How can I get aptitude to see these packages? Thanks

---

### Post by tommcd on 2009-05-09
You can just cd into /home/david/sw/wvdial directory and use:
```

sudo dpkg -i package1
sudo dpkg -i package 2

```
Do this for all the packages to install each one.

---

### Post by dLeon on 2009-05-09
Hello,
I don't think Aptitude can't do that. Except you want todo the hard way like me. It's involving making personal local Debian/Ubuntu repository folder structure (a.k.a mirror) plus editing /etc/apt/sources.list to recognize the folder we make.

So the easiest way is to install your self downloaded debs manually. The low end (master) tool is 'dpkg'. But Ubuntu/Kubuntu shiped with package that help you install debs by just doubleclick on it in file manager. Just follow the dependencies suggestion by install that dependencies first.

---

### Post by zvacet on 2009-05-09
```
cd /david/sw/wvdial
```

and then 

```
sudo dpkg -i *deb
```

---

### Post by David J Bush on 2009-05-10
Thanks, dpkg worked fine.

---

