---
title: "apt-get update error"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by desmane on 2009-01-24
SORRY THIS IS A DOUBLE POST, GO HERE: [http://ubuntuforums.org/showthread.php?t=1045123](http://ubuntuforums.org/showthread.php?t=1045123)



Hi!

after upgrading my Kubuntu 8.10 / Kde 4.1.x I get the following error: 

```
It seems that the recovery has failed. Please fix manually (try dpkg --configure -a and/or apt-get -f install) in terminal... 

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --configure, -a ], 
    Sup-process returned error code 1, 
    Error processing openoffice.org-hyphenation-en-us : subprocess post-installation script returned error exit status 127.
```

```
sudo dpkg --configure -a
Setting up openoffice.org-hyphenation-en-us (2.4-2ubuntu1) ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postinst: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us

```

```

sudo apt-get remove openoffice*
[...regex...]
The following packages will be REMOVED:
  openoffice.org-hyphenation-en-us
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142947 files and directories currently installed.)
Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I've installed the stable openoffice 3 and it worked great. I removed all openoffice packages, since then I get the error. Any idea?

THANKS!!

---

