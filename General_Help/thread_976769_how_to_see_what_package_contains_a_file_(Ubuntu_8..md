---
title: "how to see what package contains a file (Ubuntu 8.04)"
date: 2008-11-09
forum: General Help
---

### Post by gotix on 2008-11-09
how can I see what package installed a specific file? for example "/usr/bin/mc"
If I remember correct, In fedora there was something equivalent: "rpm -qf filename"

thanks

---

### Post by aurelieng on 2008-11-10
dpkg -S /usr/bin/someprogram # rpm -qif /usr/bin/someprogram
dpkg -L somepackage # rpm -ql somepackage
debsums somepackage # rpm --verify somepackage
dpkg -l '*whatever*' # rpm -qa | grep whatever

:)

---

