---
title: "Compiling trident drivers for tv-out (xfree86)"
date: 2004-11-26
forum: Hardware &amp; Laptops
---

### Post by jedthehumanoid on 2004-11-26
I have a via epia c3 system with trident cyberblade/i1 graphic card, and would like to get the tv-out for it working by installing their own driver.

I downloaded source driver for my trident from viaarena.com and unpacked xfree86 source with apt-get source xserver-xfree86; debian/rules patch-audit, then follow the instructions supplied with driver and when i try to make Makefile it complains about missing host.def file in xfree-sources

Is there anything I am missing when obtaining the sources, or anything i can to to obtain/generate host.def for my system?

 Thanks in advance! (and sorry for my bad english :P)

---

### Post by p!=f on 2004-11-26
host.def file is a part of the xutils package
```

 * 03:42:41 * pef @ agonicus *
[~] > dpkg -S host.def
xutils: /usr/X11R6/lib/X11/config/host.def

```
You may also need to install -dev packages.
```

sudo apt-get install x-dev

```

---

### Post by jedthehumanoid on 2004-12-02
Thanks for the quick reply.
Ok, apparantly xfree's and xorg's built in trident driver includes tv-out support (i just assumed i had to download tridents own driver), but the problem now is that i can't get it to work. It seems to try to initialize tv-out when i boot with the tv connected, but the tv just flickers and get a scrambled picture for a second, and then it just blacks and the tv-out signal is turned of.  

Anyone had any luck getting epia to work?  
i have searched google, the forums on viaarena, and tried with (rather gentoo specific site) epiawiki.org's xfree configuration. Both xfree86 and xorg get same result, and noone seem to have the solution...maybe i should try to compile drivers anyway...

---

