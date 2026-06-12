---
title: "PHP-PEAR"
date: 2004-10-17
forum: General Help
---

### Post by Damon on 2004-10-17
Hey All,
PHP-PEAR is not included with PHP, and I tried learning how to search through apt-get and apt-cache for packages, but no luck finding PEAR. I tried to manually install the file, but I get a whole lot of nothing
```
Loading zlib&#58; ok
Downloading package&#58; PEAR-stable......ok
Downloading package&#58; Archive_Tar-stable....ok
Downloading package&#58; Console_Getopt-stable....ok
Downloading package&#58; XML_RPC-stable....ok
Bootstrapping&#58; PEAR...................
Warning&#58; fsockopen&#40;&#41;&#58; unable to connect to cvs.php.net&#58;80 in - on line 871
download of http&#58;//cvs.php.net/co.php/pear-core/PEAR.php?p=1&amp;r=RELEASE_1_3_1 failed&#58; Connection refused &#40;111&#41;

```
Any suggestions on another way to acquire this (I.E. different apt sources, etc.)?

Thanks!

---

### Post by ulrich on 2004-10-17
have you tried downloading the deb-file from packages.debian.org and then doing an 'dpkg -i thefileiwant.deb'?
this worked for me with the unrar.debs...

hth

ulrich

---

### Post by Damon on 2004-10-17
[quote=ulrich]have you tried downloading the deb-file from packages.debian.org and then doing an 'dpkg -i thefileiwant.deb'?
this worked for me with the unrar.debs...

hth

ulrich[/quote]
Thanks for the tip... but apparently the pear server was too busy to serve me this morning. I didn't need to go the route you suggested, but I was able to find the package.  :D

---

### Post by rbreidenstein on 2008-05-27
[https://help.ubuntu.com/community/PhpPear](https://help.ubuntu.com/community/PhpPear)

---

