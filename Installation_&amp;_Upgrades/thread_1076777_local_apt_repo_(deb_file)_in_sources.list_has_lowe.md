---
title: "local apt repo (deb file) in sources.list has lower priority than http repo"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by kihjin on 2009-02-21
I have a directory of .debs and I wanted to create a local repository and use apt-get to effectively install debs from the repository. I followed the information on [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html) to create a local repository at /home/archives. Here's my sources.list:

```
$ more /etc/apt/sources.list
deb file:/home/archives /
deb http://lug.mtu.edu/ubuntu/ intrepid multiverse restricted universe main

```

I can then run (as root) **apt-get update**

```
$ apt-get update
Ign file:  Release.gpg
Ign file:  Translation-en_US
Ign file:  Release             
Ign file:  Packages            
Hit http://lug.mtu.edu intrepid Release.gpg
Ign http://lug.mtu.edu intrepid/multiverse Translation-en_US
Ign http://lug.mtu.edu intrepid/restricted Translation-en_US
Ign http://lug.mtu.edu intrepid/universe Translation-en_US
Ign http://lug.mtu.edu intrepid/main Translation-en_US
Hit http://lug.mtu.edu intrepid Release
Hit http://lug.mtu.edu intrepid/multiverse Packages
Hit http://lug.mtu.edu intrepid/restricted Packages
Hit http://lug.mtu.edu intrepid/universe Packages
Hit http://lug.mtu.edu intrepid/main Packages
Reading package lists... Done

```

But when I go to install a .deb that I know I have, apt-get still wants to download it:

```
$ ls /home/archives/xqf_1.0.5-1_amd64.deb 
/home/archives/xqf_1.0.5-1_amd64.deb
$ apt-get --print-uris install xqf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgeoip1 qstat
Suggested packages:
  geoip-bin
The following NEW packages will be installed:
  libgeoip1 qstat xqf
0 upgraded, 3 newly installed, 0 to remove and 169 not upgraded.
Need to get 1258kB of archives.
After this operation, 3744kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
'http://lug.mtu.edu/ubuntu/pool/main/g/geoip/libgeoip1_1.4.4.dfsg-2_amd64.deb' libgeoip1_1.4.4.dfsg-2_amd64.deb 642258 SHA256:be3e263ddc5c1d730f67afb48dd2c1e81fecf9357653d5b04ce3fd698290fc34
'http://lug.mtu.edu/ubuntu/pool/universe/q/qstat/qstat_2.11-1_amd64.deb' qstat_2.11-1_amd64.deb 159776 SHA256:77ac7e0c62eeed56af9bece63310f1953ca363ee3442d453ac0e479ad46b8492
'http://lug.mtu.edu/ubuntu/pool/universe/x/xqf/xqf_1.0.5-1_amd64.deb' xqf_1.0.5-1_amd64.deb 456464 SHA256:e8ff875285ad1f5bb1d73ea63f032188e5d132f766ec37ff309dd16a74590ce0

```

The local repository works if I comment out the deb http:

```
$ more /etc/apt/sources.list
deb file:/home/archives /
#deb http://lug.mtu.edu/ubuntu/ intrepid multiverse restricted universe main
$ apt-get update
Ign file:  Release.gpg
Ign file:  Translation-en_US
Ign file:  Release
Ign file:  Packages
Reading package lists... Done

```

Now if I try to install **xqf** it will use the local repository:

```
apt-get --print-uris install xqf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgeoip1 qstat
Suggested packages:
  geoip-bin
The following NEW packages will be installed:
  libgeoip1 qstat xqf
0 upgraded, 3 newly installed, 0 to remove and 169 not upgraded.
Need to get 0B/1258kB of archives.
After this operation, 3744kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
'file:/home/archives/./libgeoip1_1.4.4.dfsg-2_amd64.deb' libgeoip1_1.4.4.dfsg-2_amd64.deb 642258 MD5Sum:9e49117e35cd1033ae2c5ef9f9c0338e
'file:/home/archives/./qstat_2.11-1_amd64.deb' qstat_2.11-1_amd64.deb 159776 MD5Sum:bc703a0754dd97a187ccc47a11b356e5
'file:/home/archives/./xqf_1.0.5-1_amd64.deb' xqf_1.0.5-1_amd64.deb 456464 MD5Sum:0db7a0d18ec5a04e767c2f88836fd120

```

Does anyone know if I can get this same behavior **without** having to uncomment the http source and re-update? This doesn't seem very intuitive.

---

### Post by sehrgut on 2009-02-21
I've been struggling with the same thing. I want to (for convenience's sake) operate my local repo like you do -- as a trivial repo. Unfortunately, since pinning only works with symbolic release and section names, it only works with automatic repos, and I've yet to figure out a way to prioritise my locally-downloaded packages.

I've just now come across this problem, as this is the first time I've been trying to set up an offline Ubuntu box. If anyone has helpful hints, I'd appreciate them as well.

---

### Post by EXCiD3 on 2009-02-24
I'm interested in this as well. My next feature to add to the [Keryx Project]("http://keryxproject.org") is support for installation of the packages downloaded for the offline machines, and I think that this would most likely be the best route for installation just pointing apt to the Keryx project folder for that machine.

---

