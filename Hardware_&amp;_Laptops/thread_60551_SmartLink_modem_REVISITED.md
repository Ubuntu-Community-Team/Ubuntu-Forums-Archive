---
title: "SmartLink modem REVISITED"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by Radi0ShacK on 2005-08-28
Hi all,

i am really facing a problem in installing SmartLink modem software, i ve read most of the pots about this topic in ubuntu forums, i did use scanmodem, i did follow the steps in most of howto's and here what i ve got :

$sudo dpkg -i sl-modem*.deb

> (Reading database ... 72818 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.9a-1ubuntu2 (using sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb) ...
Unpacking replacement sl-modem-daemon ...
Unpacking sl-modem-modules-2.6.10-5-386 (from sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.10-5-386/misc/slamr.ko')
dpkg: dependency problems prevent configuration of sl-modem-daemon:
 sl-modem-daemon depends on sl-modem-modules-new | sl-modem-source (>> 2.9.6-1); however:
  Package sl-modem-modules-new is not installed.
  Package sl-modem-source is not installed.
dpkg: error processing sl-modem-daemon (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb
 sl-modem-daemon 

also i ve tried to install slmodem from source code "i ve compilled it suuccessfuly" but whenever i modprobe slamr it says cannot find slamr module !!!

so plz can any one help? Thanks Alot.

---

### Post by Radi0ShacK on 2005-08-29
plz any one can help ? cause i can't update or install any thing plz
Thanks again.

---

