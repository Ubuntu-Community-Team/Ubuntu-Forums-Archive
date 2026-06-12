---
title: "Trying to install Avant-window-navigator-0.1.1, a non-standard prefix."
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by silvernus on 2009-01-06
Hi,
  I was installing avant-window-navigator-0.1.1 package following all installation procedures.When i was configuring on terminal, the package the following problem arose..


*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' founding
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Would anybody help me to do it coz i dont knw where to start.
                             

                             Thanks...

---

### Post by Excedio on 2009-01-06
I had problems when I inatalled AWN from the terminal as well. After researching, and suggestions from others, I decided to try installing AWN through Synaptic Package Manager

System > Administration > Synaptic Package Manager

Search for Avant Window Navigator and these are the things that I have installed:

avant-window-navigator-data-trunk
avant-window-navigator-trunk
awn-extras-applets-trunk
awn-manager-trunk
libawn0-trunk
python-awn-trunk

If you encounter any problems with this method, feel free to let me know :D

---

