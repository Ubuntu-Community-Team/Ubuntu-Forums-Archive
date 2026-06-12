---
title: "XMMS doesn't start anymore"
date: 2004-12-21
forum: General Help
---

### Post by moser on 2004-12-21
Hi Folx,

I've got a problem with xmms. When I try to start it it says:

libmikmod.so.2: cannot open shared object file: Datei oder Verzeichnis nicht gefunden
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

Does anyone know how to fix that?

---

### Post by nemin on 2004-12-21
[QUOTE=moser]Hi Folx,

I've got a problem with xmms. When I try to start it it says:

libmikmod.so.2: cannot open shared object file: Datei oder Verzeichnis nicht gefunden
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

Does anyone know how to fix that?[/QUOTE]
`sudo apt-get install mikmod` worked for me :)

---

### Post by Quest-Master on 2004-12-21
Using BEEP might also be a good idea as many people prefer GTK2's nice look instead of GTK1.

sudo apt-get install beep-media-player

---

