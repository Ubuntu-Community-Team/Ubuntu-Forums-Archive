---
title: "Dpkg problems..."
date: 2005-11-10
forum: General Help
---

### Post by abominable on 2005-11-10
While trying to apt-get kmldonkey I get this problem:

dpkg: error processing /var/cache/apt/archives/kmldonkey_0.10-1_i386.deb (--unpa                                            ck):
 failed in buffer_write(fd) (8, ret=-1): backend dpkg-deb during `./usr/lib/libk                                            mldonkey.so.4.0.0': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error while cleaning up:
 unable to flush updated status of `kmldonkey': No space left on device
dpkg: failed to write status record about `libsane' to `/var/lib/dpkg/status': N                                            o space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)

What sould I do to fix it??

---

### Post by frodon on 2005-11-10
Does your linux partition is full ?

---

