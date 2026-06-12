---
title: "Problem installing tk8.4 on gutsy"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by bobhaugen on 2009-07-08
Want to install tk8.4 to use gitk.

Tried using apt-get install as well as synaptic package manager.

apt-get error message:

WARNING: The following packages cannot be authenticated!
  tcl8.4 tk8.4
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tcl8.4 8.4.15-1build1
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main tk8.4 8.4.15-1ubuntu1.1
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.15-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.15-1ubuntu1.1_i386.deb)  404 Not Found

Have tried same command yesterday and today, so if the repository is down, it's been down for awhile.

Any clues?  Thanks.

---

### Post by starcraft.man on 2009-07-08
I just checked, server seems to be up for me at this moment. Easy way to rule out a server problem is just to download from another server. 

System > Admin > Software Sources > Download From > Other

Then just select the server you want, I'm in Canada and I use uwaterloo, I know it works. You can pick the nearest server or have Ubuntu ping them all quickly to test which gives you best response.

I'm not sure I understand the authentication warning, the package is maintained in Ubuntu repos you don't need a separate key.

Are you sure it's in the regular gutsy repos? Do:

```
aptitude search tk8.4
```

```
aptitude show tk8.4
```

First searches for it in the repos, second lists info on it.

---

### Post by bobhaugen on 2009-07-08
Tried aptitude search and show, they returned info.

Tried switching to several repositories including uwaterloo.  All of them give me this error message:

[I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/I]

Followed by a list of repository indexes:

[I][http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/main/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found
[http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found[/I]

Still can't apt-get insall tk8.4

---

