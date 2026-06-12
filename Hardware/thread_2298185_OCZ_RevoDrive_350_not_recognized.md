---
title: "OCZ RevoDrive 350 not recognized"
date: 2015-10-09
forum: Hardware
---

### Post by wwynn on 2015-10-09
I am looking for steps to install an OCZ RevoDrive 350 to an Ubuntu installation on a 32GB USB stick. I have tried several times myself and have contacted OCZ tech support.

OCZ has drivers posted for three versions of Ubuntu, 12.04, 14.10 and 15.04. Their tech support says that their drivers were built with kernel 3.11, and that I should build the USB stick with the following steps before installing the RevoDrive:
[LIST]
[*]Install 12.04. (I use UUI 1.9.6.1 for this part of the installation, BTW,)
[*]Add build-essential packages: 
[http://packages.ubuntu.com/trusty/build-essential](http://packages.ubuntu.com/trusty/build-essential)
[https://packages.debian.org/sid/build-essential](https://packages.debian.org/sid/build-essential)
[*]Add DKMS packages:
[https://launchpad.net/ubuntu/+source/dkms/2.2.0.3-1.1ubuntu5.14.04.3](https://launchpad.net/ubuntu/+source/dkms/2.2.0.3-1.1ubuntu5.14.04.3)
[*]Also update all packages
[/LIST]

First attempts with the above steps are not working. Install of 12.04.05 goes ok, as does installing fromthe first link to build-essential packages. When installing from the second build-essential link, there are dependency errors. Method: download the deb packages then double-click on them. Trying to move on anyway, installling the DKMS packages also reports errors, also dependency, IIRC.

I am not committed to the above steps. I will try any steps that others have found successful.

---

