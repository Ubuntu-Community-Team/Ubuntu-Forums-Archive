---
title: "Radeon 9200 tv out"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by guyarye on 2007-08-17
I've just install Ubuntu 7.04 on my living room pc, and I have a problem:

I have ATI Radeon 9200 Pro with tv-out.
I can't get the tv-out to work (I have some weird thing going on my T.V when it's on AV (COMPUTER) channel).
Can someone point me to the right driver I need to install or the right commands I need to do?
I've installed the ATI driver from the "Add and Remove" app.

---

### Post by w4ett on 2007-08-17
Here is a how-to to enable the TV Out on the ATI cards:

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

Haven't tried it myself, but I ran across the link the other day.

Good Luck

---

### Post by lynndylan on 2007-08-17
Hey,

After following that guide with my ati 9200 SE, the image shows up on the TV clearly except for the fact that the colors appear to have their brightnes inverted.  I posted a [thread]("http://ubuntuforums.org/showthread.php?t=528227") about it but no one has responded.  Can you try it out on yours and see if you have the same problem?

Thanks,
Lynn

---

### Post by w4ett on 2007-08-17
I don't have the capability to test the TV Out at the moment.  I was wondering, have you tried to adjust the color, tint and brightness on the TV...sometimes they will have additional settings for game, movie, theatre and or live video modes...just a thought.

---

### Post by AR_Kozz on 2007-08-17
I have a radeon 9200 too and I've been trying to get tv-out to work properly for months. with fglrx I got the desktop but video would show up as black.
  So I tried that how-to, only to have the shell trip on the "autoreconf" line. (Is that part of the automake package)? Anyway, I quickly aborted when I checked the README and saw that:

[quote="README"]
  The newer Rage 128 and Radeon chips are not yet supported by this
  driver.  Rage 128's and Radeon's are, however, supported by separate
  drivers, and owners of such adapters should consult the documentation
  provided with these drivers.  This driver will also invoke the
  appropriate driver if it finds Rage 128 and/or Radeon adapter(s) in
  the system.[/quote]

This driver is for older Rage cards. No dice...

---

### Post by guyarye on 2007-08-18
I can't get the driver work. 
I'm getting this when I enter 

./autogen.sh --prefix=/usr/


src/Makefile.am:50: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:50:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:50:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:50:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:50:   its definition is in aclocal's search path.

---

### Post by guyarye on 2007-08-18
*bump*

---

### Post by lynndylan on 2007-08-18
guyarye, i had to upgrade to gutsy in order to build and install the driver properly.  It relies on x server 1.3, but feisty comes with v1.2.

---

### Post by komputes on 2008-02-20
@lynndylan: Can you please post the instructions on how you got your Radeon 9200 TV out working with Ubuntu?

---

