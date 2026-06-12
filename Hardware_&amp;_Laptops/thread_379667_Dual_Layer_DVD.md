---
title: "Dual Layer DVD"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by Geekboy on 2007-03-08
I have a Samsung SH-S182 Dual layer DVD burner.  It seems to work fine when burning standard DVDs or CDs.  I want to burn some Dual layer disks with a layer break in them.  So I installed Imgburn with Wine, and that is where I am having problems.  Imgburn says that I have not device installed, but burner works fine with Gnomebaker.

How do I verify that I have the correct drivers?  Do I need special drivers for Wine?  Is there a native linux program that will burn DL disks with a layer break?

---

### Post by Geekboy on 2007-03-08
Is there any native program that can burn dual layer with a layer break?  I'm trying to rule out the Wine/imgburn issue.

---

### Post by Erlander on 2007-03-09
I'm not sure whether DeVeDe will do this.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

Its in the repositories and is worth trying.

Rob

---

### Post by ramjet_1953 on 2007-03-09
Correct me if I'm wrong, but I thought that if you had a dual-layer DVD burner, the firmware in the burner presents the capacity of the disk to the writing software and you should be able to burn to it OK?

I have had great sucess using K3b for burning CD's and DVD's (haven't tried dual layer).

You should also have a look at K9 copy. It will compress a DVD9 source onto a DVD5 with no noticible loss in picture quality. This is a much cheaper option than using dual-layer disks.

I have noticed a glitch in K9 Copy, though. If you set it up to auto burn, it crashes and deletes the temporary file that took about an hour to create.

An easy work around is just to get it to save to an iso file and than burn that file using K3b.

By the way, both programs work fine under GNOME.

Regards,
Roger :cool:

---

