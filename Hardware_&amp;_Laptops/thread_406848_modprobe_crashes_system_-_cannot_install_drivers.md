---
title: "modprobe crashes system - cannot install drivers"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by wildbillnj1975 on 2007-04-11
Nobody on the multimedia forum has offered any ideas, so I'm crossposting it here...

I am installing the IVTV drivers on a very clean dapper system, for use with a Hauppauge PVR-150. I am following the "official" howto [here]("http://https://help.ubuntu.com/community/Install_IVTV_Dapper")

When I reach the step which says:

sudo modprobe ivtv

modprobe crashes, and the system is completely frozen. This is the second attempt - the first resulted in the kernel being so completely hosed that I resorted to a reinstall of ubuntu. I won't be able to boot into this kernel again.

Anybody know what might be going wrong? I followed the howto exactly!

After recoving the system (by dumping and re-installing the kernel) I tried it again, this time with :

modprobe -v ivtv

The first two lines are ok.
the third:

insmod /.../modules/2.6.15-28-386/ivtv/ivtv.ko

(I forget the part of the path in the ...)

It spits that out, and completely freezes - no error messages or anything.

Now the system will only boot to an older kernel (same as the first two failed attempts).
I can recover the system by reinstalling the 2.6.15-28-386 kernel and uninstalling the ivtv drivers.

Help!

---

