---
title: "Security Downloads return 404 Message"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by bill516 on 2009-02-03
Most recently Download Manager notifies me that security downloads are available for my 8.10 system.  There are four and they are:

linux headers 2.6.27-11
linux headers 2.6.27-11 generic
linux image 2.6.27-11 generic
linux libc dev

Download Manager then returns four slight variations on the following error message when it tries to download and install the four updates:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb)
  404 Not Found

Now when I boot linux I am greeted by an indication that downloads are available.  These turn out to be the same four files and they still will not download and install.

I tried using sudo apt-get upgrade.  This returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic
  linux-image-2.6.27-11-generic linux-libc-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-image-2.6.27-11-generic 2.6.27-11.26
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-image-2.6.27-11-generic 2.6.27-11.26
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-headers-2.6.27-11 2.6.27-11.26
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-headers-2.6.27-11-generic 2.6.27-11.26
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-libc-dev 2.6.27-11.26
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.26_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Aparently I do not understand the syntax for "fix missing" so I have not been able to make that work.


I have checked repositories to see if some inadvertant change had been made.  These look unaltered from what I remember being there.

If I do cat /etc/apt/sources.list this returns:


#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


Is anyone else experiencing this problem?  Is there something I should be doing or is this a repository/server issue of some sort?

My thanks for your time and help.

---

### Post by binbash on 2009-02-03
select a different mirror at synaptic (not US)

---

### Post by bill516 on 2009-02-04
> **binbash said:**
> select a different mirror at synaptic (not US)
Thank you binbash.  So I do have a server/repository issue?

I have looked at Download Manager and at Synaptic Package Manager and in both cases I do not see where I can specify a mirror or select one from a list.

My problem with the command-line at this point is that I do not know the syntax for doing what you suggest and I do not know what mirrors might be available.

Can I ask for a bit more help?

---

