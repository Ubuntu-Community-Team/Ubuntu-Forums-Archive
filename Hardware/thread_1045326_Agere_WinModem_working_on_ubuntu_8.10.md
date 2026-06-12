---
title: "Agere WinModem working on ubuntu 8.10"
date: 2009-01-20
forum: Hardware
---

### Post by marcosabel on 2009-01-20
The drivers on [http://linmodems.technion.ac.il/packages/ltmodem/sv92/]("http://linmodems.technion.ac.il/packages/ltmodem/sv92/") are for previous versions of Ubuntu. With a minor modification of the  agrsm-20080203.tar.gz package it can run on ubuntu 8.10.
The modification was to change on file serial26.c the line 1007 from this:

*struct tty_struct *tty = up->port.info->tty;*

To This:

*struct tty_struct *tty = up->port.info->port.tty;*

And that is all. 

Hope to help somebody. This issue give me many headaches

Regards.

---

### Post by macinnisrr on 2009-01-20
Thanks alot! I've been trying to get this modem working for the last week to no avail.  I'll give this a shot asap and hope for the best

---

