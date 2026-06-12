---
title: "Cannot find shared library"
date: 2008-10-16
forum: General Help
---

### Post by CharonM72 on 2008-10-16
After installing UIM 1.5.3 through source, I get the error:
uim-toolbar-gtk: error while loading shared libraries: libuim-scm.so.0: cannot open shared object file: No such file or directory

I can create a link to the file (which is in usr/local/lib) in usr/lib, and then the error changes to:

(uim-toolbar-gtk:3297): Gtk-WARNING **: cannot open display:

Any advice?

EDIT: I'm installing from source because installing through apt-get causes a different problem. Really, if I can get either of them fixed I'd be fine.
See [http://ubuntuforums.org/showthread.php?t=948090](http://ubuntuforums.org/showthread.php?t=948090)

---

### Post by CharonM72 on 2008-10-17
Fixed this problem, all I needed was a restart ](*,)
BUT I still have this problem: [http://ubuntuforums.org/showthread.php?t=948090](http://ubuntuforums.org/showthread.php?t=948090). HELP!!!  [-o<

---

