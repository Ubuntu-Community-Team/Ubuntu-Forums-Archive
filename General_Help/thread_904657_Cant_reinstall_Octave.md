---
title: "Cant reinstall Octave"
date: 2008-08-29
forum: General Help
---

### Post by kjohansen on 2008-08-29
Over the past few weeks I experimented with the kubuntu-desktop and xubuntu-desktop.  Deciding to keep gnome I followed some tutorials to completely remove the xubuntu and kubuntu desktops and associated programs.  In this process octave was uninstalled and now I cant reinstall it i get and error that I dont know what to do with.

Error after running sudo apt-get install octave:

```

(Reading database ... 117164 files and directories currently installed.)
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

---

### Post by kjohansen on 2008-08-29
well so I fixed this by doing ```
sudo apt-get install kio-umountwrapper
```

it said it was installing  kde libraries.  is there a gnome package equi to kio-umountwrapper or was this what I was supposed to do?

---

### Post by dodle on 2008-09-11
To fix fix this package, look here:  [http://ubuntuforums.org/showthread.php?p=4786808]("http://ubuntuforums.org/showthread.php?p=4786808")

---

