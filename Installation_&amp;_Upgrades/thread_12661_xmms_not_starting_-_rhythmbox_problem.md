---
title: "xmms not starting - rhythmbox problem"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by h4d on 2005-01-26
The symptoms:
```
$ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!
```

The story:
I started by installing warty from the CDs shipped to me by Ubuntu (thanks!), then changed by apt-get sources, and distro-upgraded to hoary. I never tried xmms on warty, but this is what's happening with hoary. Anyone had this problem?

Also, when I import a directory into rhythmbox, it just hangs there after a certain song. This used to happen on Fedora Core 3 as well, and apparently it is a bug on rhythmbox when loading a directory with both audio files and images (jpgs). Is there any way around this, besides installing an old version of rhythmbox?

Thanks for your time!

---

### Post by h4d on 2005-01-26
[QUOTE=h4d]The symptoms:
```
$ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!
```

The story:
I started by installing warty from the CDs shipped to me by Ubuntu (thanks!), then changed by apt-get sources, and distro-upgraded to hoary. I never tried xmms on warty, but this is what's happening with hoary. Anyone had this problem?

Also, when I import a directory into rhythmbox, it just hangs there after a certain song. This used to happen on Fedora Core 3 as well, and apparently it is a bug on rhythmbox when loading a directory with both audio files and images (jpgs). Is there any way around this, besides installing an old version of rhythmbox?

Thanks for your time![/QUOTE]
 anyone?

---

### Post by h4d on 2005-01-27
Just wanted to let you know, updating to the latest rhythmbox (0.8.8) fixed that bug about not being able to import folders containing images.

---

### Post by Buffalo Soldier on 2005-01-27
[QUOTE=h4d]Just wanted to let you know, updating to the latest rhythmbox (0.8.8) fixed that bug about not being able to import folders containing images.[/QUOTE]

Thanks for the info. I was not using Rhythmbox for quite some time. I would have totally missed knowing about the fix.

---

### Post by h4d on 2005-01-27
[QUOTE=Buffalo Soldier]Thanks for the info. I was not using Rhythmbox for quite some time. I would have totally missed knowing about the fix.[/QUOTE]
 Any word on the xmms problem?

---

### Post by sancto on 2005-02-15
hi search for and install libmikmod2 in synaptic and that will fix your problem  :-)

---

