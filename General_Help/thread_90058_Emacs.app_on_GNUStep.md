---
title: "Emacs.app on GNUStep"
date: 2005-11-14
forum: General Help
---

### Post by jvermeulen on 2005-11-14
Hello,

I wanted to try Emacs.app on GNUStep with Ubuntu 5.10 (Breezy).

[http://emacs-on-aqua.sourceforge.net/](http://emacs-on-aqua.sourceforge.net/)

The nice thing about the GNUStep version (in contrast with the default version in Ubuntu) is that it supports font anti-aliasing.

The debian package didn't work, since it depends on libgmp3 which doesn't exist in breezy. I tried compiling it myself, but that failed.

```

......
CC='gcc' CFLAGS='-MMD -MP -DGNUSTEP -DGNUSTEP_BASE_LIBRARY=1 -DGNU_GUI_LIBRARY=1 -DGNU_RUNTIME=1 -D_REENTRANT -fPIC -DGSWARN -DGSDIAGNOSE -O2 -fno-strict-aliasing -I/Library/Headers -DCANNOT_DUMP' CPPFLAGS='-D_BSD_SOURCE  -DGNUSTEP -DCANNOT_DUMP' \
  LDFLAGS='' MAKE='make'
make[1]: Entering directory `/home/jo/Desktop/emacs-20.7_ns-8.0.2/src'
Makefile:80: /Additional/base.make: No such file or directory
Makefile:81: /Additional/gui.make: No such file or directory
make[1]: *** No rule to make target `/Additional/gui.make'.  Stop.
make[1]: Leaving directory `/home/jo/Desktop/emacs-20.7_ns-8.0.2/src'
make: *** [src] Error 2
./compile: line 51: cd: GNUstep/build/Emacs.app/Resources/share/emacs: No such file or directory

```

Did anyone get this working? Tips or suggestions are greatly appreciated.

---

