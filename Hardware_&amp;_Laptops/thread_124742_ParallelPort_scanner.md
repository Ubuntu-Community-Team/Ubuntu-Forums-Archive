---
title: "ParallelPort scanner"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by keppe on 2006-02-02
I'm running Kubuntu 5.10 and trying to install a Mustek Parallelport scanner.
I followed the instructions at [http://penguin-breeder.org/sane/mustek_pp/](http://penguin-breeder.org/sane/mustek_pp/)
as follows:

1.Enable the mustek_pp backend in your dll.conf
```
$ grep mustek /etc/sane.d/dll.conf
mustek
mustek_pp
mustek_usb
```

2.Next adjust the mustek_pp.conf file to reflect your hardware setup
```
tail /etc/sane.d/mustek_pp.conf
# scanner Mustek-600-IIIEP 0x378 ccd300
#
# auto probing:
#
# scanner mustek-cis600 * cis600
# scanner mustek-cis1200 * cis1200
 scanner LT9891 * cis1200
# scanner mustek-cis1200+ * cis1200+
# scanner mustek-ccd300 * ccd300
```

3.When you have customized this file, you can verify that the driver is properly installed

When doing this as root, the scanner is being detected. When I do this as  a normal user it's not:

```
SANE_DEBUG_MUSTEK_PP=128 scanimage -L
[mustek_pp] sane-mustek_pp, version 0.13-beta. build for SANE 1.0.15
[mustek_pp] backend by Jochen Eisinger <jochen.eisinger@gmx.net>
[mustek_pp] sanei_init: auto probing port
[mustek_pp] cis_attach: couldn't attach to `parport0' (Access to resource has been denied)
```

As a workaround I now start Xsane with kdesu, but this doesn't seem the best solution to me.

I already checked the obvious things as f.i if I was well in the scanner group etc.

---

