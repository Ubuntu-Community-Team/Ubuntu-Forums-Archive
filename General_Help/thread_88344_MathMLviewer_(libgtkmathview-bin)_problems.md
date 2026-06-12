---
title: "MathMLviewer (libgtkmathview-bin) problems"
date: 2005-11-10
forum: General Help
---

### Post by Myrtti on 2005-11-10
Hello!

Me and a lot of my classmates using Ubuntu are having a XML class that includes MathML. As Ubuntu is such a lovely operating system, there is the tool mathmlviewer and mathmlsvg available. I'm not sure but at least mathmlviewer should launch a GTK program (with GUI?) that would really help us a lot. Anyways, after installing the program with apt-get ([http://packages.ubuntu.com/cgi-bin/search_packages.pl?version=breezy&keywords=gtkmathview)](http://packages.ubuntu.com/cgi-bin/search_packages.pl?version=breezy&keywords=gtkmathview)), at least I can't get the mathmlviewer to work.
I get the following error:
```

mathmlviewer: error while loading shared libraries: libgmetadom_gdome_cpp_smart.so.0: 
cannot open shared object file: 
No such file or directory
```
though gdome2-0 is installed
```
myrtti@nanook:~ $ sudo apt-get install libgtkmathview-bin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgdome2-0 libgtkmathview0c2 libt1-5
The following NEW packages will be installed:
  libgdome2-0 libgtkmathview-bin libgtkmathview0c2 libt1-5

```
and the computer does find it
```
myrtti@nanook:~ $ locate gdome
/var/lib/dpkg/info/libgdome2-0.list
/var/lib/dpkg/info/libgdome2-0.shlibs
/var/lib/dpkg/info/libgdome2-0.postinst
/var/lib/dpkg/info/libgdome2-0.postrm
/var/lib/dpkg/info/libgdome2-0.md5sums
/var/cache/apt/archives/libgdome2-0_0.8.1-1_i386.deb
/usr/share/doc/libgdome2-0
/usr/share/doc/libgdome2-0/MAINTAINERS
/usr/share/doc/libgdome2-0/README
/usr/share/doc/libgdome2-0/changelog.gz
/usr/share/doc/libgdome2-0/copyright
/usr/share/doc/libgdome2-0/changelog.Debian.gz
/usr/lib/libgdome.so.0.8.1
/usr/lib/libgdome.so.0

```
I'd try to make a symlink to the correct location, but I don't know which file to symlink and where is the correct location. Any ideas?

---

### Post by Myrtti on 2005-11-10
So the problem appears to be that there is actually a library missing.
[http://gmetadom.sourceforge.net/](http://gmetadom.sourceforge.net/)

---

### Post by Myrtti on 2005-11-10
mmmkay, a little chat with our friends ompaul and thoreauputic 
made me sudo apt-get install libgdome2-cpp-smart0c2

After that...```

myrtti@nanook:~ $ mathmlviewer
Usage: mathmlviewer [options] file ...

  -V, --version                 Output version information
  -d, --debug                   Debug mode
  -h, --help                    This small usage guide
  -v, --verbose[=0-3]           Display messages

```
So it does work, I think.
Now the problem is that I can't remember what I was supposed to do with this anymore :D

---

