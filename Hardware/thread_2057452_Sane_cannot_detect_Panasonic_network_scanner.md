---
title: "Sane cannot detect Panasonic network scanner"
date: 2012-09-13
forum: Hardware
---

### Post by salvadortiz on 2012-09-13
Hi, I am trying to install a network scanning service Panasonic KX-MB all-in-one., but cannot get xsane or scanimage to see my scanner.

So far, I have:

1. installed the libsane-panamfs-1.0.0-i386.deb package from
[http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html](http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html) (had to use --force-architecture, since I have 10.4 64b)

2. edited /etc/sane.d/panamfs.conf (which comes in the .deb above), adding a line "net <scanner-ip>"

3. edited /etc/sane.d/saned.conf, adding a line with <scanner-ip>

4. added the "service sane-port" (found in so many howtos) block to /etc/xinetd.conf

5. Added another block to /etc/hal/fdi/policy/saned.fdi

And always.... nothing. In other words, I have reached my highest level of ineptitude!

I have the impression I haven't "told" the system where is the driver it should use (usr/lib/sane/libsane-panamfs.so.1.0.0), but I have no idea how and where to something like this.

Could anybody offer a clue?

Thanks, a lot,

Salvador

BTW, I know the scanner works, because some people use it from Windows (it's a scanner at work, but we don't hace any Linux support here). Also, the printer works fine under Linux and Windows.

---

