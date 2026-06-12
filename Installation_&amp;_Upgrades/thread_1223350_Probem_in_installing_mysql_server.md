---
title: "Probem in installing mysql server"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by vksingh.iiitb on 2009-07-26
Hi all, I am trying to installl mysql server using synaptic manager in Ubuntu.
 
I am getting the error below: ** /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb: subprocess pre-installation script returned error exit status 1**
 
**Kindly help!**

---

### Post by Partyboi2 on 2009-07-26
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the outputs to
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by vksingh.iiitb on 2009-07-26
> **Partyboi2 said:**
> Hi, can you open a terminal (Applications>Accessories>Terminal) and post the outputs to
```
sudo dpkg --configure -a
sudo apt-get -f install
```
[B]dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server

[/B]The above error is comming. I believe I will have to install mysqlserver-5.0 first

---

### Post by vksingh.iiitb on 2009-07-26
> **vksingh.iiitb said:**
> [B]dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server

[/B]The above error is comming. I believe I will have to install mysqlserver-5.0 first
The following error is comming in installing mysql-server-5.0
 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by vksingh.iiitb on 2009-07-26
> **vksingh.iiitb said:**
> The following error is comming in installing mysql-server-5.0
 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
If I try to install mysql-server-5.0 from synaptic package manager, I am getting the error: 

[B]E: /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb: subprocess pre-installation script returned error exit status 1
[/B]

---

