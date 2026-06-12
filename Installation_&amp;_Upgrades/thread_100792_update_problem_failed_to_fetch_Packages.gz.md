---
title: "update problem: failed to fetch Packages.gz"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by humean on 2005-12-08
I'm having problems with 'apt-get update'. I get this output:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [3028kB]

gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Fetched 19.8kB in 7s (2575B/s)
Reading package lists...
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



Is something wrong with the server?

---

### Post by humean on 2005-12-08
I just tried a new sources file and I get a similar or the same problem:

-----
/etc/apt/sources.list
--
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic

# Ubuntu supported packages (packages)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse


-----
apt-get update
--
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy Release
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy/main Packages
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Ign http://us.archive.ubuntu.com breezy/universe Packages
Get:5 http://us.archive.ubuntu.com breezy/multiverse Packages [91.9kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Get:6 http://security.ubuntu.com breezy-security/universe Packages [9388B]
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Get:7 http://security.ubuntu.com breezy-security/multiverse Packages [1187B]
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Get:8 http://us.archive.ubuntu.com breezy-updates/universe Packages [8204B]
Get:9 http://us.archive.ubuntu.com breezy-updates/multiverse Packages [708B]
Get:10 http://us.archive.ubuntu.com breezy/universe Packages [3028kB]
99% [10 Packages gzip 0]                                            8439B/s 0s
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 131kB in 7s (16.9kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by humean on 2005-12-09
Somebody on #ubuntu helped me, I had to remove the 'us.' prefix from the universe lines.

---

