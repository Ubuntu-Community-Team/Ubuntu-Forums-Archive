---
title: "Error applying maintenance to 8.04.1"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by todivefor on 2009-08-25
I was applying maintenance to my 8.04.1 system and got the following error.  I have never had an error before applying maint.  Can someone please explain how to resolve error?

(Reading database ... 180752 files and directories currently installed.)
Preparing to replace linux-headers-2.6.24-24 2.6.24-24.53 (using .../linux-headers-2.6.24-24_2.6.24-24.59_all.deb) ...
Unpacking replacement linux-headers-2.6.24-24 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.24-24_2.6.24-24.59_all.deb (--unpack):
 unable to install new version of `./usr/src/linux-headers-2.6.24-24/include/asm-mips/mach-jazz': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.24-24_2.6.24-24.59_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by todivefor on 2009-08-26
Bump

---

### Post by todivefor on 2009-08-26
Is the mach-jazz directory causing my problem?

drwxr-xr-x 2 root root  4096 2009-08-25 14:43 mach-ip32
d????????? ? ?    ?        ?                ? mach-jazz
d????????? ? ?    ?        ?                ? mach-jmr3927
d????????? ? ?    ?        ?                ? mach-lasat
drwxr-xr-x 2 root root  4096 2009-06-26 09:23 mach-lemote

---

### Post by slakkie on 2009-08-26
I think it is, those dirs with all the question marks doesn't look to promising. Do a fsck on that filesystem/disk. Remove/rename the dirs if possible and redo the install/upgrade.

---

