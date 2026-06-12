---
title: "Package build question"
date: 2008-09-24
forum: General Help
---

### Post by gjk on 2008-09-24
I was attempting to prepare the necessary dependencies in order to build mail-notification 5.4 from source. I am running Ubuntu 8.04. The readme particular to mail notification instructs me to execute ./jb configure prior to building.
A few packages were missing such as msgfmt and dbus-binding-tool which seemed easy enough to figure out and load via apt-get but I am now stuck not fully understanding the warnings and error which indicates that GNOME can not be found. (I am running Gnome desktop 2.22.3)

Any assistance & clarification is greatly appreciated. I posted this under launch pad and I am posting it hear hoping it is more of a generic environment issue that this community can explain to me.

Thanks
Gary

gary@ByTheSea:~/Projects/mail-notification-5.4$ ./jb configure
checking for ngettext(), dgettext(), bind_textdomain_codeset() in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for scrollkeeper-preinstall... /usr/bin/scrollkeeper-preinstall
checking for scrollkeeper-update... /usr/bin/scrollkeeper-update
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for the OMF directory... /usr/share/omf
checking for the ScrollKeeper database directory... /var/lib/scrollkeeper
checking for dbus-binding-tool... /usr/bin/dbus-binding-tool
checking for gob2... not found
checking the C compiler dependency style... GCC
checking for the GNU C library... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GNOME... no
WARNING: Package gconf-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `gconf-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'gconf-2.0' found
WARNING: Package libgnomeui-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libgnomeui-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libgnomeui-2.0' found
WARNING: Package gnome-vfs-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `gnome-vfs-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'gnome-vfs-2.0' found
WARNING: Package libglade-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libglade-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libglade-2.0' found
WARNING: Package libxml-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libxml-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libxml-2.0' found
WARNING: Package libnotify was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libnotify.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libnotify' found
ERROR: unable to find GNOME

---

### Post by Ryadt on 2008-09-24
Try```
sudo aptitude install gconf2 libgconf2-dev
```

---

### Post by gjk on 2008-09-26
thanks for the suggestion but no joy.
I still get most of the same warnings and error. It seems to indicate an erroneous environment setting and not a missing package. At least that is the way I am reading it. With that said gconf2 is no longer in the warning list since I followed Ryadt's suggestion. I'll check to see if each of the mentioned packages exist on my system.....

checking for pkg-config... /usr/bin/pkg-config
checking for GNOME... no
WARNING: Package libgnomeui-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libgnomeui-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libgnomeui-2.0' found
WARNING: Package gnome-vfs-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `gnome-vfs-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'gnome-vfs-2.0' found
WARNING: Package libglade-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libglade-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libglade-2.0' found
WARNING: Package libxml-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libxml-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libxml-2.0' found
WARNING: Package libnotify was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `libnotify.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'libnotify' found
ERROR: unable to find GNOME

---

### Post by gjk on 2008-10-04
Just wanted to provide feedback to close out my original question.
I did indeed need to install additional DEV packages. The packages required were:
libgnomeui-dev
libnotify-dev
libglade2-dev

Thanks

---

### Post by Francewhoa on 2010-03-14
The installer is hard to find on the internet so I attached it at [http://ubuntuforums.org/showpost.php?p=8966724&postcount=6](http://ubuntuforums.org/showpost.php?p=8966724&postcount=6)

---

