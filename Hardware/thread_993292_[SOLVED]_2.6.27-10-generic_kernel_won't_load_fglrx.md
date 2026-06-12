---
title: "[SOLVED] 2.6.27-10-generic kernel won't load fglrx driver"
date: 2008-11-25
forum: Hardware
---

### Post by horde on 2008-11-25
I just upgraded to the 2.6.27-10-generic kernel from the repositories using Adept, and when I rebooted it didn't seem to be able to load the driver.  Even attempting to run in low-graphics mode didn't work.  Nor did dpkg --reconfigure, nor did booting into root shell and running envyng -t.  However, loading the 2.6.27-8-generic kernel instead works.

I'm running a Dell Inspiron 9400, Kubuntu 8.10, ATI Mobility Radeon X1400 using the latest fglrx from repositories.

Anyone else having this problem/know how to resolve it?

Thanks.

---

### Post by b.q.wemer on 2008-11-28
Hi, 

maybe you inherit some crap from former versions. Move the /var/lib/dkms/fglrx directory to your home-folder as a backup. Then purge everything that has to do with fglrx, reinstall xorg-driver-fglrx and restart Xserver. At least this worked for me. 

HTH

---

### Post by horde on 2008-11-28
Thank you, thank you, thank you, b.q.wemer.  I did as you said (backed up and removed /var/lib/dkms/fglrx) and let envyng do the rest...unfortunately I'm not comfortable configuring/installing kernel modules yet.

But it works now...2.6.27-10-generic now loads fglrx.  Now if they'll just ship a driver that has X11/3D acceleration on Xorg 1.5 I'll be completely happy with my setup.

Much appreciation for your help!

---

