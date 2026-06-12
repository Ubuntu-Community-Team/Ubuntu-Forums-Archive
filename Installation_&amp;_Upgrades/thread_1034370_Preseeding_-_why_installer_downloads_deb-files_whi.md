---
title: "Preseeding - why installer downloads deb-files which are availible in pool/main..."
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by gencaslan on 2009-01-08
Im trying to preseed my installation. 

this is from my preseed file

tasksel tasksel/first multiselect ubuntu-standard, openssh-server, samba-server, lamp-server

allthough packages are avalible in pool/main

> root@ubuntu:/home/omc# ls /opt/cd-image/pool/main/m/mysql-dfsg-5.0/
libmysqlclient15-dev_5.0.51a-3ubuntu5.1_i386.deb  mysql-client_5.0.51a-3ubuntu5.1_all.deb       mysql-server_5.0.51a-3ubuntu5.1_all.deb
libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb   mysql-common_5.0.51a-3ubuntu5.1_all.deb
mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb      mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb

he still downloads e.g. mysql-client-5.0 and mysql-server-5.0


why ? 

any ideas ? 

thx

---

### Post by kranny on 2009-01-08
Ive never done this but a small suggestion..why dont u put your deb files in /var/cache/apt/archives and do sudo apt-get update followed by the install

---

### Post by albinootje on 2009-01-08
> **gencaslan said:**
> 
he still downloads e.g. mysql-client-5.0 and mysql-server-5.0


Are they downloaded from security.ubuntu.com ?
If so, then it's because newer "security updated" versions were available.

---

### Post by gencaslan on 2009-01-08
> **albinootje said:**
> Are they downloaded from security.ubuntu.com ?
If so, then it's because newer "security updated" versions were available.

Yes sir, they come from security.ubuntu.com. 

how can i prevent this ? 

download the apropriate file and put it in the remastered cd ? there are a lot of files...

or is there an option to prevent the installer downloading newer versions ? 

thx

---

### Post by albinootje on 2009-01-08
> **gencaslan said:**
>  or is there an option to prevent the installer downloading newer versions ? 


You should get the newest versions, but if you only want to use the cdrom then make sure that the lines for the cdrom are the only ones which are uncommented in /etc/apt/sources.list.
Edit it with :
```

sudo nano /etc/apt/sources.list

```
And run :
```

sudo apt-get update

```
after that.

---

