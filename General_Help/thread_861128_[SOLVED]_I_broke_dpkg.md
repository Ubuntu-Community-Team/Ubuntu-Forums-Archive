---
title: "[SOLVED] I broke dpkg"
date: 2008-07-16
forum: General Help
---

### Post by The Midnight Coder on 2008-07-16
I dunnoe what to do now..........I think its because the ups failed and the system went off after i installed g++

Look: > 
fabian23@fabian23-desktop:~$ sudo apt-get remove dillo
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  dillo
0 upgraded, 0 newly installed, 1 to remove and 164 not upgraded.
After this operation, 1114kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
fabian23@fabian23-desktop:~$ 


---

### Post by sisco311 on 2008-07-16
Try to restore the /var/lib/dpkg/available file: 

```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo apt-get update
```

---

### Post by The Midnight Coder on 2008-07-16
Error:
> fabian23@fabian23-desktop:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
cp: cannot stat `/var/lib/dpkg/available-old': No such file or directory
fabian23@fabian23-desktop:~$ 

---

### Post by sisco311 on 2008-07-16
post the output from:
```
ls /var/lib/dpkg/
```
and
```
ls /var/backups
```

---

### Post by The Midnight Coder on 2008-07-16
ls /var/lib/dpkg/
> 
fabian23@fabian23-desktop:~$ ls /var/lib/dpkg/
alternatives  diversions-old  parts             status      updates
cmethopt      info            statoverride      status-old
diversions    lock            statoverride-old  triggers
fabian23@fabian23-desktop:~$ 


ls /var/backups
> 
fabian23@fabian23-desktop:~$ ls /var/backups
dpkg.status.0     dpkg.status.2.gz  dpkg.status.4.gz  gshadow.bak  passwd.bak
dpkg.status.1.gz  dpkg.status.3.gz  group.bak         infodir.bak  shadow.bak
fabian23@fabian23-desktop:~$ 


---

### Post by sisco311 on 2008-07-16
Try to create a new (empty) /var/lib/dpkg/available file:
```
sudo -i
echo "" > /var/lib/dpkg/available
exit
sudo apt-get update
```

---

### Post by The Midnight Coder on 2008-07-16
That worked but I got this error after I ran sudo apt-get remove dillo:

>  dpkg: serious warning: files list file for package `g++' missing, assuming package has no files currently installed. 

---

