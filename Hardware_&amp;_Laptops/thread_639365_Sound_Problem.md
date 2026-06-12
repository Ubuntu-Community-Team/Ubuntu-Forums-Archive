---
title: "Sound Problem"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by betamax on 2007-12-13
Hello,

I've just recently installed Gutsy on a Samsung R45 laptop.
Working a treat besides sound which just won't play nice.

I've been into the sound settings and set it to use the OSS analog device, still no joy.
Is there a module I need to be excluding which may be causing this ?

If I get change I'll have a search through the forum.

Cheers,

:confused:

---

### Post by uberlube on 2007-12-13
HP has a support webpage that offers all the drivers for all their products, perhaps Samsung offers the same?

---

### Post by seawright on 2007-12-13
If Samsung don't provide any Linux drivers you could always check the oss drivers provided by [www.4front-tech.com](www.4front-tech.com). I use them with Gutsy though not on a laptop. They used to be closed source so tended to be shunned by the os community but the source code for most of their drivers was released under GPL2 earlier this year.

Temüjin has written an article about installing them. You can find it here:

[http://ubuntuforums.org/showpost.php?p=3768914](http://ubuntuforums.org/showpost.php?p=3768914)

One thing it doesn't point out is that as ALSA is being removed you need to install package 
libesd0 to replace libesd-alsa0.

---

### Post by betamax on 2008-01-02
Hello,

Thanks for the advice.

I finally get my sound working :)
Edited my /etc/modprobe.d/alsa-base to include the following:

**options snd-hda-intel position_fix=1 model=laptop-eapd**

Once I did this it all worked sweet.

Thanks again for any help.

---

