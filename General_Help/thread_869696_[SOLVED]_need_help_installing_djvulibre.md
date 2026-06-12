---
title: "[SOLVED] need help installing djvulibre"
date: 2008-07-25
forum: General Help
---

### Post by jmd9qs on 2008-07-25
hi,

i've downloaded the djvulibre tar.gz, and got it extracted. then i swithced to the new directory and used "./configure", which it did with no problem. however, when i try "make" or "make install", the comp says 


make[2]: Leaving directory `/home/jmd9qs/djvulibre-3.5.20/i18n/ja'
make[1]: Leaving directory `/home/jmd9qs/djvulibre-3.5.20/i18n'
( cd desktopfiles && make install )
make[1]: Entering directory `/home/jmd9qs/djvulibre-3.5.20/desktopfiles'
/usr/bin/install -c -d /usr/local/share/djvu/osi/desktop
/usr/bin/install -c register-djvu-mime /usr/local/share/djvu/osi/desktop
/usr/bin/install: cannot stat `register-djvu-mime': No such file or directory
make[1]: *** [install-djvu-files] Error 1
make[1]: Leaving directory `/home/jmd9qs/djvulibre-3.5.20/desktopfiles'
make: *** [install-desktopfiles] Error 2

****  Installation failed. Aborting package creation.

---

