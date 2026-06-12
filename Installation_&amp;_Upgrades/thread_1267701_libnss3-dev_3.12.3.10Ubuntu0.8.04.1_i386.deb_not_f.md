---
title: "libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb not found"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-09-16
I am trying to install install_flash_player_10_linux.deb on ubuntu 8.04 but i am geting the following error

Failed to fetch [http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb](http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb)  404 not found

---

### Post by zvacet on 2009-09-16
Probably just temporary server is down.

---

### Post by hoboy on 2009-09-16
> **zvacet said:**
> Probably just temporary server is down.

I have point my browser to 

 have point my browser to 
[http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb](http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb)

I get the following error
DNS was not found.
The link is damaged

---

### Post by zvacet on 2009-09-17
You can install flash even if you still get that error,because flash is not in security repo.Edit your source list typing in terminal

```
gksudo gedit /etc/apt/sources.list
```

look if you have this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

if look like this

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

just remove # sign and save and close file.

```
sudo apt-get update
```

In synaptic search for adobe-flashplugin and install it.Remove all previous version you have like flashplugin-nonfree.
Compare your source list with [this.]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#sources.list")You can use it if you want.

---

