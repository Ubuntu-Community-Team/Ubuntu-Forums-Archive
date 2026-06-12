---
title: "[SOLVED] kio-umountwrapper problem"
date: 2008-09-11
forum: General Help
---

### Post by dodle on 2008-09-11
```
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not sure why my system keeps trying to uninstall this package, but it is very annoying.  I was removing packages that I never use to clear some space on my / partition, and now I keep getting the error above any time I try to install/uninstall something.  I've checked all the dependencies, and they are all installed.  Is there a way to fix this?

Edit:
```
:~$ sudo dpkg-reconfigure kio-umountwrapper
/usr/sbin/dpkg-reconfigure: kio-umountwrapper is broken or not fully installed

```

Edit:
I apologize for not searching before posting.  I found the answer here:  [http://ubuntuforums.org/showthread.php?p=4786808]("http://ubuntuforums.org/showthread.php?p=4786808")

---

