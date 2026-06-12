---
title: "amule: error while loading shared libraries: libwx_gtk-2.4.so.0"
date: 2005-11-19
forum: General Help
---

### Post by Wowi on 2005-11-19
Amule binary package (2.0.3-1ubuntu4 from breezy/universy repository) doesn't seem to work.

I installed amule:
```
sudo apt-get install amule
```
and then tried to execute it, it gives error message:
**amule: error while loading shared libraries: libwx_gtk-2.4.so.0: cannot open shared object file: No such file or directory**

There is no package providing this file when I tried to search with Package Contents Search: [http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libwx_gtk-2.4.so.0&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libwx_gtk-2.4.so.0&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386")

However, there is /usr/lib/libwx_gtk-2.4.so.1.0.0 so I tried to make symlink:
```
sudo ln -s /usr/lib/libwx_gtk-2.4.so.1.0.0 /usr/lib/libwx_gtk-2.4.so.0
```

That didn't help, because after that amule gave error message:
**amule: relocation error: amule: symbol _ZN17wxEventTableEntryC1ERKiiiM8wxObjectFvR7wxEventEPS2_, version WXGTK_2.4 not defined in file libwx_gtk-2.4.so.0 with link time reference**

So I removed that symlink and uninstalled amule.

Then I tried to compile/install amule from source package:
```
sudo apt-get build-dep amule
sudo apt-get -b source amule
sudo dpkg -i amule_2.0.3-1ubuntu4_i386.deb
```

After that the results are the same:
**amule: error while loading shared libraries: libwx_gtk-2.4.so.0: cannot open shared object file: No such file or directory**

Am I the only one having this problem?

---

