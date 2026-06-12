---
title: "how to specified the installation directory."
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by calvinlyp on 2009-05-27
hi all,

i am relatively new to ubuntu platform thus alot of commands are very new to me.

i am trying to install a software called sharc from [http://sourceforge.net/projects/sharc/](http://sourceforge.net/projects/sharc/)

it sta in the INSTALL file that:

======================================================
Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

======================================================

i need to change the default location to /usr/bin

how do i go about doing it?
or how to use the command option of `--prefix=PATH'.??

i try using the command below:
sudo make install --prefix=/usr/bin

but it generate error.

pls help.

thanks.

---

### Post by glotz on 2009-05-27
[QUOTE=calvinlyp]You can specify an
installation prefix other than `/usr/local' by giving `**configure**' the
option `--prefix=PATH'.[/QUOTE]
;) Not make.

---

