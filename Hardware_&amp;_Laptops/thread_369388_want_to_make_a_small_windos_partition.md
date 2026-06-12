---
title: "want to make a small windos partition"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by gtkourounis on 2007-02-24
ok, so i have already installed ubuntu on my laptop (100% linux) but now i have decided that i want to make a small space on my hard drive for windows and i am not quite sure how to do that from ubuntu without having to reinstall all of ubuntu again (which i dont really feel like doing)

do you guys have any answers????

thanx in advance

---

### Post by Ek0nomik on 2007-02-24
To my knowledge, if you want to run both Windows and Linux, it would be easier to install Windows first, and than Linux.  The reason being:  Windows will screw around with your MBR (Master Boot Record), and will take over your boot up sequence.  Essentially, you won't have an option to boot into Windows or Ubuntu if you install Windows last.

Now, you could install Windows after, but I believe that will require messing around in GRUB to make sure you can choose whether you want to go into Ubuntu or Windows.  It can be done, it just takes work, and I for one haven't done it.

I hope this helps!

---

### Post by Ek0nomik on 2007-02-24
I guess I kinda avoided  your real questions though.

If you want to get a Windows place on your harddrive, you just need to make another partition.

How did you setup your partitions for Ubuntu?

All you need to do is put in the Ubuntu Live CD, and you can change your partitions around.  I believe Windows XP requires around 5GB minimum for install, so keep that in mind.

Cheers!

---

### Post by gtkourounis on 2007-02-24
thank you, i managed to get the double boot going but i did had to uninstall ubuntu and then install windows and then install ubuntu again.

thanx again

---

