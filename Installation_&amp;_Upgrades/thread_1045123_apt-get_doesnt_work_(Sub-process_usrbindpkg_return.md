---
title: "apt-get doesnt work (Sub-process /usr/bin/dpkg returned an error code)"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by desmane on 2009-01-20
Hello people, 

my package manager is broken, this is "ok" because it never happend before, ever. I wasn't able to fix this myself, hope you can help me. 

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up openoffice.org-hyphenation-en-us (2.4-2ubuntu1) ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postinst: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am using Kubuntu Intrepid 8.10, KDE 4.1.x, 2.6.27-11-generic

openoffice should be completely removed (apt-get purge openoffice.org*)

THANKS!!

---

### Post by Partyboi2 on 2009-01-20
Have you tried
```
 sudo apt-get remove --purge openoffice.org-hyphernation-en-us 
```

---

### Post by desmane on 2009-01-24
thanks for your reply, that doesnt work either. 


```
sudo apt-get remove --purge openoffice.org-hyphenation-en-us
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  openoffice.org-hyphenation-en-us*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142947 files and directories currently installed.)
Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can't ignore anymore, installing new software doesnt work too!

---

### Post by desmane on 2009-01-24
fixed: [http://ubuntuforums.org/showthread.php?t=698140](http://ubuntuforums.org/showthread.php?t=698140)

---

### Post by Partyboi2 on 2009-01-24
> **desmane said:**
> fixed: [http://ubuntuforums.org/showthread.php?t=698140](http://ubuntuforums.org/showthread.php?t=698140)
:lolflag: that link shows how bad my memory can be. :p

---

### Post by vckeating on 2009-09-03
I had the same issue - but the instructions from this page worked for me:

[https://bugs.launchpad.net/openoffice/+bug/274556](https://bugs.launchpad.net/openoffice/+bug/274556)

- V

---

