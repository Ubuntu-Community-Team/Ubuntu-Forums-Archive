---
title: "Opera won't start"
date: 2005-11-11
forum: General Help
---

### Post by K2712 on 2005-11-11
I just installed opera, but when I click on the icon nothing happened.  So I went to the terminal and this is what I get, but I'm not sure what to make of it.  Any ideas??

jeff@Laptop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.50-20050916.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
jeff@Laptop:~$

---

### Post by corstar on 2005-11-11
mine won't start either.  The error I get is 'segmentation fault'
I'll let you know if I find the cause.

---

### Post by lupo on 2005-11-13
same to me. When I try to start Opera I get an "segmentation fault" error. :(

---

### Post by pickarooney on 2005-11-13
No idea about the segmentation faults, but for the errors in the first post you need to install two packages.
**sudo apt-get install libqtm3** might be the first one, if not use synaptic nd search for packages resembling that.
for the second, you need a java package, look up jre or j2re or jdk in synaptic.

---

### Post by Xian on 2005-11-13
Make sure you have the lesstif2, libmotif3, & libqt3-mt packages installed.
Next, install this version of Opera: 

[opera_8.50-20050916.6-shared-qt-etch-i386.deb](http://ftp.sunet.se/pub/www/clients/Opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb)

---

### Post by dolny on 2005-11-13
I've got a question? Did you install: [http://www.ubuntuforums.org/showthread.php?t=82025&page=3](http://www.ubuntuforums.org/showthread.php?t=82025&page=3) VLC Player maybe? Because it didn't work for me until I uninstalled some broken VLC packages. o_O

---

