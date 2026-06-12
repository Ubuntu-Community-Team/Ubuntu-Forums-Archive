---
title: "installing deinstalled packages ?"
date: 2008-10-01
forum: General Help
---

### Post by a.dehqan on 2008-10-01
In The Name Of God
Hello

I'll be so Thankfull if you guide me .
I want to install packages with deinstall statue.
First, i got list of deinstalled packages with commond :

```
dpkg --get-selections | grep -w deinstall > file
```
Then ;
```
dpkg --set-selections < file
```
Then ;
```
dselect update
```
Then i tried to install them with this commond
```
dselect install
```

but, in case number of packages is 278 ,it wanted to install just one (that is not deinstalled package) package ,see :

```
Reading package lists...
Building dependency tree...
The following NEW packages will be installed:
  libhal-storage-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.4kB of archives.
After unpacking 393kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

How can i install those 278 packages ?

regards dehqan

---

### Post by a.dehqan on 2008-10-03
in The Name Of God
Hello


i have fixed that probllem with using " dpkg --clear-selections
" befor --set .
Now when i try "dpkg --set-selections < file && dselect install" ,i face this :

```
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libgcc1 (due to apt) libstdc++6 (due to apt) debian-archive-keyring (due
  to apt) base-files bash
0 upgraded, 0 newly installed, 729 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1737MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 
```

How can i install those 278 .deinstalled packages just ?

regards dehqan

---

