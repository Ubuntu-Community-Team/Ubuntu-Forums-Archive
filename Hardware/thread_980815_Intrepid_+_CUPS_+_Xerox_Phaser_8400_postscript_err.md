---
title: "Intrepid + CUPS + Xerox Phaser 8400: postscript error"
date: 2008-11-13
forum: Hardware
---

### Post by wpoely on 2008-11-13
Hi,

Before upgrading to intrepid, printing worked just fine: cups with the xerox drivers for the phaser 8400dp. After upgrading tot intrepid, i can't print anymore from evince, acroread, openoffice, ... I always get: "No %%Pages: comment in header!". The strange thing is, when i use commandline lpr on the same pdf, it does print! A look on the logs learns me that it has something todo with postscript but i don't really understand what i can do about it. In attachment, there are 2 logs: good and bad. In good you see the output when i print on commandline with lpr. In bad you see what i get when printing with evince.

Can anyone help?

Thanks in advance!

---

### Post by wpoely on 2008-11-14
It's fixed :)

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/289759](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/289759)

---

