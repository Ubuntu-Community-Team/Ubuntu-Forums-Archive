---
title: "files and packages correspondence"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by ilna on 2009-08-02
Hi! Two related questions:

1. Say, I have installed a package'rezound'. How to list all files were installed during the package installation?

2. Say, there is installed file '/usr/bin/rezound'. How to find a package to which this concrete file belongs to ?

---

### Post by zvacet on 2009-08-02
1.system>admin>synaptic>find package and right click on it>properties>installed files

2.> If you want to install a package, and you can&#8217;t find out what it is called by searching with
apt-cache, but know the filename of the program itself, or some other filename that belongs
to the package, then you can use apt-file to find the package name. This is done like this:
     $ apt-file search filename
It works just like dpkg -S, but will also show you uninstalled packages that contain the file. It
could also be used to find what packages contain necessary include files that are missing when
compiling programs, although auto-apt is a much better method of solving such issues, see
&#8216;How to install packages &#8220;on demand&#8221;&#8217; on the facing page.
You can also list the contents of a package, by running:
     $ apt-file list packagename
apt-file keeps a database of which files all packages contain, just like auto-apt does and it
needs to be up-to-date. This is done by running:
     # apt-file update


Taken from [here.]("http://www.debian.org/doc/manuals/apt-howto/")

Install apt-file from synaptic.After that run from terminal
```
updatedb
```

---

### Post by ilna on 2009-08-02
apt-file (I prefer CLI) works fine, thanks!

---

