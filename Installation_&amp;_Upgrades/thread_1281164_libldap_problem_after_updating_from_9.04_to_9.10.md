---
title: "libldap problem after updating from 9.04 to 9.10"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Nick Mitin on 2009-10-03
After updating from 9.04 to 9.10 beta samba, transmission, pfroftpd and mediatomb won't start:



# /etc/init.d/samba start
* Starting Samba daemons

/usr/sbin/nmbd: relocation error: /usr/lib/libldap_r-2.4.so.2: symbol gnutls_certificate_get_x509_cas, version GNUTLS_1_4 not defined in file libgnutls.so.26 with link time reference

Does anyone know how to fix this?

---

### Post by mwawrin on 2009-12-08
Hi,

I hit a similar issue when upgrading from KUbuntu 9.04 to 9.10, but with Kontact.  I solved it for myself just now, so thought I'd share in case the situation is similar for you or others.

The problem for me was that libldap_r-2.4.so.2 was picking up a 'bad' version of libgnults that I apparently had on my system.   

Running ldd on libldap_r-2.4.so.2 I found that it was picking up libgnults from /usr/local/lib:

```

$ ldd /usr/lib/libldap_r-2.4.so.2 |grep libgnutls
        libgnutls.so.26 => /usr/local/lib/libgnutls.so.26 (0x00110000)

```

You can use the following command to see whether or not the symbol in question is defined in the library or not.

```
$ nm -D <libgnuttls file> |grep gnutls_certificate_get_x509_cas
```

In my case, the libgnutls.so file under /usr/local/lib did not define this symbol, and since libldap was picking up this library I hit the undef. symbol.   I can't for the life of me remember why I had these libs installed here.  The libgnutls.so under /usr/lib did export this symbol.

```
$ nm -D /usr/lib/libgnutls.so |grep gnutls_certificate_get_x509_cas
00026640 T gnutls_certificate_get_x509_cas
```

Either setting LD_LIBRARY_PATH=/usr/lib in my env, or removing the offending libs from /usr/local/lib make kontact run again.

Hope this helps.

Matt.

---

