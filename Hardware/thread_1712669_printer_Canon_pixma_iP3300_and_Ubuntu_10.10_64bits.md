---
title: "printer Canon pixma iP3300 and Ubuntu 10.10 64bits"
date: 2011-03-23
forum: Hardware
---

### Post by Fiable.biz on 2011-03-23
Hello. 

I unfortunately have a Canon Pixma iP3300 and Canon only provides a driver for RPM style 32 bits Linux distributions... In 2009, thanks to jcl_vanier's help, I managed to have it work with 64 bits Mandriva: 
[http://forum.mandriva.com/fr/viewtopic.php?p=713553#713553](http://forum.mandriva.com/fr/viewtopic.php?p=713553#713553) 
There are old instructions for Ubuntu: 
[http://ubuntuforums.org/showthread.php?t=374898](http://ubuntuforums.org/showthread.php?t=374898) given by Jim Connachan 
but my Ubuntu 10.10 is 64 bits. Moreover, following the instructions, I get the following error messages: 

$ sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common 
[sudo] password for henri: 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Unable to locate package libxml1 
E: Unable to locate package libgtk1.2 
E: Couldn't find any package by regex 'libgtk1.2' 
E: Unable to locate package libgtk1.2-common 
E: Couldn't find any package by regex 'libgtk1.2-common' 

Newer versions (libxml2, libgtk2.0-0, libgtk2.0-common) are installed in my system. Unlike Mandriva's tool to install packages, Synaptic package manager doesn't say if the packages are 32 or 64 bits, so I'm lost.

If I ignore these errors concerning the librairies and go on, using cnijfilter-ip3300-2.70-2.i386.rpm instead of cnijfilter-ip3300-2.70-1.i386.rpm, then alien pretends that cnijfilter-common_2.70-2_i386.deb and cnijfilter-ip3300_2.70-3_i386.deb have been generated and I get no error message, but I can't see them and I get an error message at the next step: 

sudo dpkg -i *.deb 
dpkg: error processing *.deb (--install): 
cannot access archive: No such file or directory 
Errors were encountered while processing: 
*.deb

I then installed 32 bits library like this:
$ sudo aptitude install ia32-libs

but got no improvement.
Any idea to make that printer work with 64 bits Ubuntu would be welcome.

---

### Post by walt.smith1960 on 2011-03-23
_deleted_
[]("http://support-sg.canon-asia.com/P/search?model=PIXMA+iP3300&menu=download&filter=0&tagname=g_os&g_os=Linux")

---

