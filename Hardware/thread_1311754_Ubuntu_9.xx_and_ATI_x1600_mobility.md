---
title: "Ubuntu 9.xx and ATI x1600 mobility"
date: 2009-11-02
forum: Hardware
---

### Post by pjani on 2009-11-02
Hy i have one question. If i downgrade(becouse there is no more drivers for latest xorg) Gnome and xserver what futures do i loose?:(

---

### Post by lavinog on 2009-11-02
when you say that there are no more drivers, are you refering to the proprietary driver (fglrx).
The open source ati driver should work for your card.

To answer your question, you will be better off installing 8.10 instead of spending hours/months hacking everything to work with a downgraded xorg.  The list of dependancies for gnome and xorg are huge.

Is the open source driver not working for you?

---

### Post by pjani on 2009-11-02
Hmm, i dont know how to uninstall all old drivers and then install fglrx. currently I'm running mesa drivers they are slow as hell and very cpu consuming driver.

In old 6.10 i didnt have any troubles with fglrx.:o

---

### Post by lavinog on 2009-11-02
your card is no longer supported by fglrx as of 9.04.
8.10 should offer to install fglrx for you.

The open source drivers in 9.10 should work pretty good, but 3d support may be limited.  (3d works pretty good with my 200m, but won't work at all with my newer 3650.)

you may want to post your /var/log/Xorg.0.log

---

### Post by ssri on 2009-11-02
> **pjani said:**
> Hy i have one question. If i downgrade(becouse there is no more drivers for latest xorg) Gnome and xserver what futures do i loose?:(

You would have to downgrade the kernel too since the last Catalyst driver that supports your card recognizes kernels up to 2.6.28.  I've seen a patch for 2.6.29.  Since Karmic ships with 2.6.31, you would have to downgrade your kernel too and the rest of its dependencies (not a wise decision).  You can either go back to intrepid or use Jaunty with a downgraded xserver like myself ;).

---

### Post by pjani on 2009-11-03
Why cant xorg run with older graphic drivers?

---

### Post by lavinog on 2009-11-03
because the older drivers do not conform to the newer standards.
The newer standards are put in place to improve performance and reliability.

---

