---
title: "How about fglrx &amp; swusp2 ?"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by sir_tomek on 2005-04-19
Hallo,

As it is known, current kernell suports "regular" software suspend.
Together with acpid scripts and Xorg ati driver it all works ok
with my IBM T42p. But, even having vbetool enabled (uncommented
in prepare.sh - as it commes commented out with by default)
resuming after hibernation with fglrx driver does not work that well.
(The os works, but graphics is sloooow - so one needs to restart X server).

Now - there are reports that people got fglrx working with software suspend 2
and vbetool ([http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00366.html)](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00366.html)).

I have tryed to repeat steps described. But applying swusp2 patch to plain
kernel (plain version of 2.6.10 ubuntu kernel) and then ubuntu patches
and after that hacking a bit to resolve rejections does not give the
expected result: fglrx + swusp2 + vbetool = freeze after resume.

I am not a kernel hackar, and probably not a hacker at all, so
very likely I'm doing something wrong.

The question is then:
Is it possible to incorporate swusp2 into official ubuntu kernel in a
"proper and concious" way, and this way hopefully enable users
of laptops with ati graphics to have fully functional (and supported) systems ?

Regards,
Tomek

---

### Post by ricadelic on 2005-07-29
You have to set EnableVbetool yes in hibernate.conf

see [http://linux.com.hk/PenguinWeb/manpage.jsp?section=5&name=hibernate.conf](http://linux.com.hk/PenguinWeb/manpage.jsp?section=5&name=hibernate.conf)

It works for me.

Cheers,
Rick

---

