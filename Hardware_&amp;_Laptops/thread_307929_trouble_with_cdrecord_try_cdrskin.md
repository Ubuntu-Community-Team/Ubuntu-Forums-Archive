---
title: "trouble with cdrecord? try cdrskin"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by brightbyte on 2006-11-27
After failing to get cdrecord (and in effect, k3b and other burning programs) to work with my laptop's CD burner (cdrecord says LG GMA-4082N, the laptup is an ASUS F3J), I finally found the solution: **use libburn + cdrskin** instead. cdrskin emulates the command line interface of cdrecord, using libburn as a backend. So it can seemlessly be used as a replacement for cdrecord in most places. 

A description of how to use cdrskin with k3b is  [here]("http://scdbackup.sourceforge.net/k3b_on_cdrskin.html"), I have also added a quick run down to the [K3B Howto]("https://help.ubuntu.com/community/K3BHowto") - no idea if that was the right place, maybe it gets (re)moved. 

If you can't find libburn and cdrskin in the package manager, add *deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit backports contrib* to /etc/apt/sources.list (if you use dapper, replace edgy-pouit with dapper-pouit)

HTH

---

### Post by brightbyte on 2006-11-27
Addendum: I just realized that the package is called **libburn2** - sorry for that.

---

### Post by vicarious on 2007-02-04
Thank you. None of the Gnome burning apps worked for me and when I manually used cdrecord it would sometimes work and sometimes not work between kernel updates.

I would be nice if Gnome apps could use cdrskin instead of cdrecord for a backend. :)

---

