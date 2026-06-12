---
title: "Samsung SATA DVD Writer - Can't write."
date: 2009-01-02
forum: Hardware
---

### Post by shankariyer on 2009-01-02
Hello,

I fixed a new SATA Samsung DVD Writer SH-S223F. Ibex finds the drive and when ever
I try to burn a blank CD, DVD, it always says insert a blank media, these are brand new
blank media.

Please advice,
Thanks.

---

### Post by TheLions on 2009-01-02
which burning program are you using? Did you try burner with some other OS?

---

### Post by shankariyer on 2009-01-02
CD/DVD Creator from GNOME and Brasero. Same drive worked flawlessly in Windoze.

---

### Post by FrankVdb on 2009-01-04
I'm having the same problem with Intrepid, it's driving me crazy. I can read my DVD drives (i.e. they get mounted) but I cannot burn anything. I'm also running Virtualbox and Virtualbox is seeing my drives but somehow cannot mount them.

Afaik, both of my DVD drives are directly connected to SATA controllers (I'm on a brand-new system).

---

### Post by shankariyer on 2009-01-04
My case is sort of fixed.

First on my environment, I had 2 SATA DVD writers ( LiteOn and Samsung ), one SATA HDD, 2 IDE HDD's.

I unplugged the LiteOn drive, which never worked and Samsung started to work, at least partially, in the sense that it burned couple of DVD's and then started to give errors. The irony is still there is no problem with this Samsung drive, on Windoze with Nero.

I believe, there is something going on with the Ibex and SATA controller. The very same media that Ibex/CD-DVD Creator or Brasero complain, burns well under Windoze.

I'm tired of making too many toasters :)

---

### Post by FrankVdb on 2009-01-04
I'm seriously considering going back to Hardy. There are other people with similar problems on the Virtualbox forum and there doesn't seem to be any solution.

---

