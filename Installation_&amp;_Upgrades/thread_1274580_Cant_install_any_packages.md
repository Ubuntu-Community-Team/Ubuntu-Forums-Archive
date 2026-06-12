---
title: "Cant install any packages"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by TheDigitalNinja on 2009-09-24
When i do any apt-get commands or try synaptic i get a ton of 404 errors, yet i can ping the ip addresses and use the server for everything else.

here is my result for an apt-get update

rperkins@webserv:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  404 Not Found
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  404 Not Found
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  404 Not Found
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Partyboi2 on 2009-09-24
Hi, Edgy has reached its end of life, I would suggest upgrading to a later version (hardy, intrepid, jaunty). You will probably find doing a clean install of a later release will be a lot easier then trying to upgrade.

---

### Post by earthpigg on 2009-09-24
hi,

Edgy is no longer officially supported.

[http://en.wikipedia.org/wiki/Ubuntu_releases#Ubuntu_6.10_.28Edgy_Eft.29](http://en.wikipedia.org/wiki/Ubuntu_releases#Ubuntu_6.10_.28Edgy_Eft.29)
> Ubuntu 6.10 (Edgy Eft), released on 26 October 2006,[24][25] was Canonical's fifth release of Ubuntu. Ubuntu 6.10's support ended on 25 April 2008.

what that means is Ubuntu's servers for edgy are shut down on their end.

you will either need to use an unofficial repository or, preferably, do a fresh install of a current version.

8.04 *Long Term Support* will be supported until April 2011. (3 years of support from release)
9.04 will be supported until October 2010. (18 months of support from release)

10.04 *Long Term Support* will be released in the _4_th month of 20_10_ and probably be supported until April 2013. (3 years of support from release)

---

