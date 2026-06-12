---
title: "Can not install with synaptic."
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by kmb101 on 2009-01-19
I get this error when trying to download of update.(see below) I am not sure why it happened it worked fine last night.I think it has something to do with my wireless driver firmware. I can get the package I just can't install it. Does anyone know what I can do? I tried command line also. Thanks in advance for your help.



(Reading database ... dpkg: error processing /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `b43-fwcutter': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2009-01-19
Maybe try to clean the cache first.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Make sure you don't have synaptic open when you run those commands or it will complain about unable to lock...

---

### Post by kmb101 on 2009-01-19
Hey thanks for the info. Everything works great until I try to upgrade, then I get the same error message. Any other ideas?? Thanks!!


(Reading database ... dpkg: error processing /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `b43-fwcutter': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2009-01-19
Clean your cache again with the **sudo apt-get clean**.  Then, go into synaptic and change to another server to see if that fixes the problem.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

---

### Post by Partyboi2 on 2009-01-19
> **kmb101 said:**
> I get this error when trying to download of update.(see below) I am not sure why it happened it worked fine last night.I think it has something to do with my wireless driver firmware. I can get the package I just can't install it. Does anyone know what I can do? I tried command line also. Thanks in advance for your help.



(Reading database ... dpkg: error processing /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `b43-fwcutter': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
There seems to be a problem with the list file for b43-fwcutter, try moving the list file out of the way
```
sudo mv /var/lib/dpkg/info/b43-fwcutter.list /var/lib/dpkg/info/b43-fwcutter.list.old 
```
then
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kmb101 on 2009-01-19
It almost had me going but then when I tried to update again I got this error. It didn't work. Thanks


E: /var/cache/apt/archives/base-files_4.0.1ubuntu5.8.04.4_i386.deb: failed in buffer_read(fd)

---

### Post by kmb101 on 2009-01-19
> **Partyboi2 said:**
> There seems to be a problem with the list file for b43-fwcutter, try moving the list file out of the way
```
sudo mv /var/lib/dpkg/info/b43-fwcutter.list /var/lib/dpkg/info/b43-fwcutter.list.old 
```
then
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

This is the error I get when I do this.

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Partyboi2 on 2009-01-19
> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory Make sure that there are know other package managers like update manager, synaptic package manager open when executing those commands.

---

### Post by kmb101 on 2009-01-19
Thank You, Thank You! That worked!!! Have a great week.

---

