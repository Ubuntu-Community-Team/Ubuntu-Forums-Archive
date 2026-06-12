---
title: "apt-get update: Sub-process bzip2 returned an error code (2)"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by Sarek on 2006-01-09
Just a quick question here. I run ```
apt-get update
``` as usual and I get the following:

```
~$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Get:3 http://us.archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:5 http://public.planetmirror.com breezy Release.gpg
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy-backports Release
Hit http://us.archive.ubuntu.com breezy Release
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Get:6 http://public.planetmirror.com breezy Release
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Ign http://public.planetmirror.com breezy Release
Hit http://us.archive.ubuntu.com breezy-backports/main Packages
Hit http://us.archive.ubuntu.com breezy-backports/restricted Packages
Get:7 http://public.planetmirror.com breezy/free Packages
Hit http://us.archive.ubuntu.com breezy-backports/universe Packages
99% [7 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://public.planetmirror.com breezy/free Packages
  Sub-process bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Get:8 http://public.planetmirror.com breezy/non-free Packages
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
99% [8 Packages bzip2 0] [Connecting to us.archive.ubuntu.com (216.165.129.138)]bzip2: (stdin) is not a bzip2 file.
Err http://public.planetmirror.com breezy/non-free Packages
  Sub-process bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Fetched 113kB in 5s (19.0kB/s)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://public.planetmirror.com breezy Release: Unknown error executing gpgv
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

What has happened?

---

### Post by aysiu on 2006-01-09
Maybe your sources.list is too cluttered?
See the first link of my sig.

---

