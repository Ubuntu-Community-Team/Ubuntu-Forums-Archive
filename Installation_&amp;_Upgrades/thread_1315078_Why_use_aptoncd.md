---
title: "Why use aptoncd ?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-11-04
Hey all,

I had upgraded to 9.10 from 9.04 and had created aptoncd before and after the upgrade. As the upgrade crashed [from an alternate cd] I tried a fresh install and used the aptoncd created after the upgrade. It did not install anything and just copied the debian packages to the /var/apt/cache [At least, this is what i understood]. Now my questions are :-

1. Is there a way to get all my installed packaged from the aptoncd to the new fresh install OFFLINE?

2. If one cannot restore the installed application as the above case, why aptoncd is required ? A backup of the /var/apt/cache anywhere in the unformatted partition of the harddisk will do the same restore.

3. Also let me know if I can do something using the 9.04 Live CD, aptoncd [both before and after upgrade] and 9.10 alternate cd.

I had a lot of applications installed and even remembering the list is impossible. Also there is the cost for data download charged by my ISP.

I am waiting for a reply before starting individual downloads. 

Any help will be highly appreciated.

---

### Post by muscularsage on 2009-11-05
aptond as far as i know does NOT INSTALL the softwares that u have attempted to take backup.aptoncd copies as uve said to the cache directory.after that whn u open synaptic and reload those files det added to the list .but am not sure if that wil allow u to install offline but try with some small software and checkout!

---

