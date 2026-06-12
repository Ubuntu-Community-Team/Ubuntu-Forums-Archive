---
title: "Sony VAIO motioneye webcam"
date: 2009-02-08
forum: Hardware
---

### Post by geltonas on 2009-02-08
Hi, I am new in linux world, and I need some help from a side becouse I dont know much about  linux configurations, and there is problem:

my hardware:
Bus 001 Device 003: ID 05ca:1836 Ricoh Co., Ltd 

and tried to download cam drivers for interprid using these commands:
  wget [https://launchpad.net/%7Eintuitivenipple/+archive/ppa/+files/r5u870-dkms_0.11.1-0ubuntu1~ppa2i_all.deb](https://launchpad.net/%7Eintuitivenipple/+archive/ppa/+files/r5u870-dkms_0.11.1-0ubuntu1~ppa2i_all.deb)
sudo dpkg -i r5u870-dkms_0.11.1-0ubuntu1~ppa2i_all.deb

during installation I got error:


Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic -C /lib/modules/2.6.27-11-generic/build M=/var/lib/dkms/r5u870/0.11.1/build.....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: error processing r5u870-dkms (--install):
 subprocess post-installation script returned error exit status 10
Processing triggers for man-db ...
Errors were encountered while processing:
 r5u870-dkms


I read that I need to change log:

r5u870-dkms (0.11.1-0ubuntu1~ppa2i) intrepid; urgency=low

  * debian/rules: fix - install firmware files to correct directory.

any idea how can I change that log?

or problem is somewhere else?


thanks in advance

---

