---
title: "synaptic/apt-get"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by nkingcade on 2005-12-19
All,

I want to install an upgraded version of a utility I use in class (nmap-3.95). I currently have 3,81 installed. So here is the problem:

1. I would like to use the CLI and the apt-get command to do the upgrade and install. Is that possible.

2. If I chose to use the synaptic package manager, how do I point it to the insecure site to get the upgrade. 

I remember reading about the use of both methods. I just don't know where to find the information. Can someone help set me straight? Thanks.

Neal

---

### Post by NotJustANewbie on 2005-12-19
1. WIth apt-get it installs it all for you. Just do
```
sudo apt-get install [name of package]
```

2. As for the insecure site, I wouldn't. I'd go for the Ubuntu Backport repository.
To change your repositories, just do
```
sudo gedit /etc/apt/source.list
```

---

### Post by nkingcade on 2005-12-19
OK! what is the backport area? I attempted and understand the syntax of the apt-get commands. My problem is that I cannot get the tool to download from the site where the tarball resides. I've gone to the source file and attempted to edit in a line that points to insecure(it's fine from a security standpoint, I've scanned). I want to be able to upgrade to nmap 3.95. Can I do this by pointing the sourcelist to insecure? Or go through a backport mechanism? Come back??

Neal

---

### Post by az on 2005-12-19
nmap 3.93 is in Dapper rightnow.  You can always just grab that version, or install it from source.

To install the Dapper binary, you will have to upgrade some packages on your system to dapper (unstable, not reccommended right now)

To install the dapper source, you can either add the dapper universe deb-src entry in your sources.list, update and

apt-get build-dep nmap

and

apt-get source -b nmap

and that should build the deb package for you which you can then install
sudo dpkg -i nmap*.deb

---

### Post by nkingcade on 2005-12-20
Azz,

Thanks for the reply. I was wondering? Would it be easier to download the sources from insecure and compile it myself? Is there a particular convention used to store  the source code in Ubuntu?

Neal

---

### Post by az on 2005-12-20
[QUOTE=nkingcade]Azz,

Thanks for the reply. I was wondering? Would it be easier to download the sources from insecure and compile it myself? Is there a particular convention used to store  the source code in Ubuntu?

Neal[/QUOTE]


You can absolutely compile it yourself.  It just will not be part of the package manager.  Everything else on your system will be handled by the package manager, so there will not be something preventing another package from overwriting things from your custom-compiled app.

You can make it into a deb package by using checkinstall.  That works for very simple applications and is not foolproof.  Debian packaging is very sophisticated.

---

### Post by nkingcade on 2005-12-20
Thanks Azz.

Neal

---

