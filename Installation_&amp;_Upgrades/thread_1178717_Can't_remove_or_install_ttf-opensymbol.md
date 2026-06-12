---
title: "Can't remove or install ttf-opensymbol"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by frigginacky on 2009-06-04
When I upgraded to Jaunty, the ttf-opensymbol package didn't install correctly.  I'm currently unable to reinstall or remove the package. Both result in similar errors:

```

~$ sudo apt-get remove ttf-opensymbol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-opensymbol
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 500kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210246 files and directories currently installed.)
Removing ttf-opensymbol ...
Updating fontconfig cache...
Bus error
dpkg: error processing ttf-opensymbol (--remove):
 subprocess post-removal script returned error exit status 135
Errors were encountered while processing:
 ttf-opensymbol
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

~$ sudo apt-get install ttf-opensymbol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-opensymbol is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-opensymbol (1:3.0.1-9ubuntu3) ...
Updating fontconfig cache...
Bus error
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
 ttf-opensymbol
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas on how to fix this?  I'd really like to get this package working, since I can't install OpenOffice without it.  Thanks in advance!

---

### Post by zvacet on 2009-06-05
```
sudo dpkg --configure -a
```

---

### Post by frigginacky on 2009-06-05
I tried that to no avail.  However, I've just done a clean install of Jaunty (I had numerous unresolved issues from the upgrade), so it's moot point now.  Thanks though.

---

