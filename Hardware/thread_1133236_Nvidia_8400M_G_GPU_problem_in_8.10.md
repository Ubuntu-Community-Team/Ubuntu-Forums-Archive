---
title: "Nvidia 8400M G GPU problem in 8.10"
date: 2009-04-22
forum: Hardware
---

### Post by yakipa on 2009-04-22
Hi,
I'm trying to activate the gpu for a long time. I'm exhausted :) When I installed restricted drivers, Gnome running in low graphics mode and it says "Failed to load the NVIDIA kernel module!" I've also tried some different methods (manually,Envy), but I can't get it worked. What should i do?

Thanks for any help!!

---

### Post by hotweiss on 2009-04-22
Yes, the 8400 needs newer drivers. I would just wait for a few more hours until Ubuntu 9.04 released, it will support the 8400.

---

### Post by hotweiss on 2009-04-22
Yes, the 8400 needs newer drivers. I would just wait for a few more hours until Ubuntu 9.04 released, it will support the 8400.

If you can't wait:

1)Download the drivers

2) CTRL-ALT-F1

3) sudo /etc/init.d/gdm stop

4) sudo apt-get remove Nvidia*

5) sudo sh ./Nvidiawhateverthedriveris

6) sudo /etc/init.d/gdm restart

---

### Post by yakipa on 2009-04-22
OK. I'm waiting for the upgrade. Thank you..

---

### Post by yakipa on 2009-04-23
I've upgraded my ubuntu to 9.04, it is still not recognize the gpu. So I've tried this.> 1)Download the drivers

2) CTRL-ALT-F1

3) sudo /etc/init.d/gdm stop

4) sudo apt-get remove Nvidia*

5) sudo sh ./Nvidiawhateverthedriveris

6) sudo /etc/init.d/gdm restart
In installation it gives an error > ERROR: Unable to load the kernel module 'nvidia.ko'. And installation fails.

---

### Post by hotweiss on 2009-04-23
> **yakipa said:**
> I've upgraded my ubuntu to 9.04, it is still not recognize the gpu. So I've tried this.
In installation it gives an error  And installation fails.

Try installing the driver using Envy:

1) sudo apt-get remove Nvidia*

2) sudo aptitude purge envyng

3) sudo aptitude purge envy

4) sudo rm -R /usr/share/envy

5) sudo apt-get install envyng-core

6) CTRL-ALT-F1

7) sudo /etc/init.d/gdm stop

8) sudo envyng -t

9) sudo /etc/init.d/gdm restart

Don't worry if steps 2 -4 give you errors. I really don't know what elese could work after this. Let me know what your results are.

---

