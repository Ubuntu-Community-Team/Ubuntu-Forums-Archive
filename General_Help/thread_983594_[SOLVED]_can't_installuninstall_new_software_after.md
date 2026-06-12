---
title: "[SOLVED] can't install/uninstall new software after intalling an alien version monode"
date: 2008-11-15
forum: General Help
---

### Post by garybrlow on 2008-11-15
After wanting to try out the latest monodevelop alpha 
[monodevelop-1.9-3.novell.noarch.rpm]("http://ftp.novell.com/pub/mono/download/noarch/monodevelop/1.9-3/monodevelop-1.9-3.novell.noarch.rpm")       I downloaded the official rpm from monodevelop, used alien to make a deb and installed it. There was an error regarding configuration since it was looking for a suseconfig module but nevertheless the IDE worked fine. I wanted to install some other debs of other programs but installation fails due to the suseconfig error. Tried to uninstall monodevelop itself but the error remains. Now I'm stuck not being able to install or uninstall anything. Some please help, I tried all of the apt and dpkg troubleshooting procedures but still the same.

Error Details:
```

(Reading database ... 109326 files and directories currently installed.)
Removing monodevelop ...
-e 
ERROR: SuSEconfig or requested SuSEconfig module not present!

dpkg: error processing monodevelop (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 monodevelop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by directhex on 2008-11-16
rm /var/lib/dpkg/info/monodevelop.postrm

And don't use Alien again.

---

### Post by garybrlow on 2008-11-16
Kewl it was finally uninstalled and I can install new/other software again!!!! Thanks!!!

---

