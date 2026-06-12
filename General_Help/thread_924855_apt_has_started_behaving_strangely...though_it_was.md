---
title: "apt has started behaving strangely...though it was working fine earlier.."
date: 2008-09-20
forum: General Help
---

### Post by shredder12 on 2008-09-20
I have Hardy installed on my system.
Earlier everything was working fine..but now i m having problem in using apt-get...
whenver i try the following commands.
```
sudo apt-get update
sudo apt-get install <package name>
```
i always get the following response.
```
Err http://archive.ubuntu.com hardy Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/main Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/universe Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/main Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/universe Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Ign http://archive.ubuntu.com hardy Release
Ign http://in.archive.ubuntu.com hardy Release
Ign http://in.archive.ubuntu.com hardy-updates Release
Ign http://security.ubuntu.com hardy-security Release
Ign http://archive.ubuntu.com hardy/main Sources
Ign http://in.archive.ubuntu.com hardy/main Packages
Ign http://in.archive.ubuntu.com hardy/universe Sources
Ign http://in.archive.ubuntu.com hardy/main Sources
Ign http://in.archive.ubuntu.com hardy/multiverse Sources
Ign http://in.archive.ubuntu.com hardy/universe Packages
Ign http://in.archive.ubuntu.com hardy/multiverse Packages
Ign http://security.ubuntu.com hardy-security/main Packages
Ign http://archive.ubuntu.com hardy/restricted Sources
Ign http://in.archive.ubuntu.com hardy-updates/main Packages
Ign http://in.archive.ubuntu.com hardy-updates/universe Sources
Ign http://in.archive.ubuntu.com hardy-updates/main Sources
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Ign http://in.archive.ubuntu.com hardy-updates/universe Packages
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Err http://in.archive.ubuntu.com hardy/main Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/multiverse Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hardy/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://security.ubuntu.com hardy-security/main Sources
Ign http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://security.ubuntu.com hardy-security/universe Packages
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Err http://archive.ubuntu.com hardy/restricted Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy/multiverse Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/main Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/multiverse Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://in.archive.ubuntu.com hardy-updates/multiverse Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/main Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/multiverse Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com hardy-security/multiverse Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IN.bz2  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Earlier it was working absolutely fine..
i don't know why..but now a days it has started giving these problems..
it has nothing to do with the internet connection because everything seems to work absolutely fine say  elinks, firefox, synaptic..everything works just fine..
I even searched for it on the forums and tried to modify my /etc/resolv.conf file. I even checked the file with another person who has ubuntu 7.10 and everything works fine  on his system ( i checked it just to make sure that the connection setting were all right as we have same internet connection ) but i found no problem.
I access internet through a proxy server.
and 2 DNS servers.
**I will greatly appreciate any help in this matter..**

---

### Post by adult swim on 2008-09-20
someone else was having this problem earlier.  try chaging your source to the main server from system>administration>synaptic package manager and then choose settings>repositories and change download from to main server.

---

### Post by shredder12 on 2008-09-20
i changed the settings to download from main server..but the problem still persists..

---

