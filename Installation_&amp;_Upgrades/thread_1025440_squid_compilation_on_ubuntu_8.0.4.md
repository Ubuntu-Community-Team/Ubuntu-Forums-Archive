---
title: "squid compilation on ubuntu 8.0.4"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by it_suppport on 2008-12-30
Dear All,

I want to install squid3.0-stable9 on ubuntu server, as ubuntu provides stable1 release. 
Can someone tell me how to compile & install the same on ubuntu server
so far I've done following. Let me know if I'm on right track or not
installed the required build-essential.
installed checkinstall
compiled the squid with ./configure --prefix=/usr/loca/squid --with-default-user=squid
make all
make install
But it seems not yet installed on my system.

Can someone tell me where am I missing?

---

### Post by Partyboi2 on 2008-12-30
make sure you are in the source directory and type:
```
./configure --prefix=/usr/loca/squid --with-default-user=squid
```Then make sure that there are no errors before proceeding with
```
make
```again make sure there are no errors then use checkinstall
```
sudo checkinstall
```
Edit: I think you can install it using apt-get without having to compile
```
 sudo apt-get install squid3
```

---

### Post by it_suppport on 2008-12-30
apt-get install squid3 gives me STABLE1 release
I want to install latest STABLE version

---

### Post by it_suppport on 2009-01-02
wonders!, if no one knows it??

---

