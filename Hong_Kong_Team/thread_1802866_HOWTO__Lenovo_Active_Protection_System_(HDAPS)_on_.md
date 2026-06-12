---
title: "HOWTO : Lenovo Active Protection System (HDAPS) on Ubuntu 11.04"
date: 2011-07-12
forum: Hong Kong Team
---

### Post by samiux on 2011-07-12
Lenovo ThinkPad or alike comes with Active Protection System (HDAPS) in order to protect your hard drive from being damaged by shock.  This feature is designed for Windows system.  Thanks for the open source developers, we can use this feature on your Ubuntu 11.04 box now.

The installation is simple, easy and straight forward.

The tutorial is [here]("http://samiux.blogspot.com/2011/07/howto-lenovo-active-protection-system.html").

Enjoy!

Samiux

---

### Post by jfouclait on 2012-05-04
hey!
I've tried this metod but id doesnt work for me. 
I have a lenovo e520 with 12.04 ubuntu.
if i follow instructions i get stuck at step 3 that returns:

sudo modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/3.2.0-24-generic/updates/dkms/tp_smapi.ko): No such device or address

sudo /etc/init.d/hdapsd restart
 * Restarting IBM Hard Disk Active Protection System (HDAPS) daemon hdapsd                                                                                      Fri May  4 07:26:27 2012: Starting hdapsd
Fri May  4 07:26:27 2012: Could not find a suitable interface

any help?
thx

---

### Post by samiux on 2012-07-05
> **jfouclait said:**
> hey!
I've tried this metod but id doesnt work for me. 
I have a lenovo e520 with 12.04 ubuntu.
if i follow instructions i get stuck at step 3 that returns:

sudo modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/3.2.0-24-generic/updates/dkms/tp_smapi.ko): No such device or address

sudo /etc/init.d/hdapsd restart
 * Restarting IBM Hard Disk Active Protection System (HDAPS) daemon hdapsd                                                                                      Fri May  4 07:26:27 2012: Starting hdapsd
Fri May  4 07:26:27 2012: Could not find a suitable interface

any help?
thx

Sorry for late reply as I seldom here now.

I have tested my Lenovo ThinkPad X200 and it works great.  Maybe E520 use different hardware.

Samiux

---

