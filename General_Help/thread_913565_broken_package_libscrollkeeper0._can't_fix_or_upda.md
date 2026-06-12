---
title: "broken package: libscrollkeeper0. can't fix or update"
date: 2008-09-07
forum: General Help
---

### Post by employeeno5 on 2008-09-07
Hi everyone. Recently when attempting to install something and discovered I had a broken package. I tried apt-get -f install without success.

Here's my output.
```
[~]! sudo apt-get -f install
[sudo] password for broderick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libscrollkeeper0
The following NEW packages will be installed:
  libscrollkeeper0
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/27.9kB of archives.
After this operation, 1376kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 32090 package `libscrollkeeper0':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any suggestions? Is there anything I can do to my /usr/bin/dpkg file to help this?

I'm currently unable to install or update any other software because of this is presenting a few fairly urgent problems. If anyone can offer any advice or guidance it would be hugely appreciated.

Thanks!!

---

### Post by tuxxy on 2008-09-07
Do you have this package installed

[http://packages.ubuntu.com/hardy/libscrollkeeper0](http://packages.ubuntu.com/hardy/libscrollkeeper0)

---

### Post by iaculallad on 2008-09-07
On your terminal:

-Create a backup of your status file:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.original
```

-Delete the status file:
```
sudo rm /var/lib/dpkg/status
```

-Copy the -old status file:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
sudo apt-get -f install

```

---

### Post by employeeno5 on 2008-09-07
Thank you iaculallad!

I was hoping I could do exactly that, and it did indeed work. I didn't want to try messing with any of those files those as I previously have not encountered them and did not know exactly what they were.

Thanks very much for your help. This is speediest response I've ever had to an issue. 

I've said it before and I'll say it again; these forums are the greatest!

Thanks again!

---

### Post by iaculallad on 2008-09-07
You're very much welcome and don't be afraid tinkering config files - just be sure to create a backup file for it just in case it won't resolve the issue. Just come back if new issues arises in your Ubuntu usage, the forum got plenty of helping hands.

---

