---
title: "broken files"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Phil in WBL MN on 2009-07-29
Package manager and update manager indicate two broken files. When I go to package manager to filter for broken:
  Linux Image generic  2.6.28.14.19   installed version 2.6.28.14.19
  and
  Linux-restricted-modules 2.6.28-14 generic  installed version 2.6.28.14.19
 

 Are broken  I choose to reinstall and I get the following message.
 

 

 E: /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-14-generic/kernel/drivers/scsi/53c700.ko')
 

 Should I remove this from the cache and run update manager hoping it to download a new copy?

---

### Post by ajgreeny on 2009-07-29
In synaptic choose **Edit -Fix Broken Packages** rather than just try to reinstall and you should be OK.

---

### Post by stlsaint on 2009-07-29
or boot from disc and choose to start in safe mood and from there re-install broken packages!!!

---

### Post by Phil in WBL MN on 2009-07-29
I tried the Synaptic Program manager . did not fix the broken file. 
As it is in the cache if I remove it will synaptic download a replacement?

---

### Post by ajgreeny on 2009-07-30
Yes it should do, and if the original .deb is corrupt, perhaps that will solve the problem.  Worth a try.

---

