---
title: "Graphics driver installed, but still low rez ?"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by chocon on 2008-04-12
Hello, I tried to installed graphics driver for my Dell XPS M1530, the card is NVDIA Geforce 8600gm. I followed all the steps required (run the .run file downloaded from their site, install libc for building kernel), then at the end, I got the message "Unable to perform the runtime configuration check for lib 'libGL.so.1' (/usr/lib32/libGL.so.169.12') assuming successful installation". But still my screen resolution is 640x480, and I can't change it. Any idea/experience about this problem, pls help, thanks.

---

### Post by seventeener on 2008-04-12
That's funny, i've also been struggling with this for the last 10 hours... I'm running hardy amd64 on dell d830 with nVidia Quadro NVS 135M. Here's what helped me.
I couldn't remove nvidia-glx-new through the synaptics manager, but it should be removed since it intersects in some files with the drivers from nvidia.com. So I logged out from X into a command line terminal, then made

killall gdm

sudo apt-get remove nvidia-glx-new

and then run the driver installation as suggested at nvidia.com, i.e.

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

(maybe you'll have another driver version)
good luck!
PS I still had the message "Unable to perform the runtime configuration check for lib 'libGL.so.1' (/usr/lib32/libGL.so.169.12') assuming successful installation" at the end, but anyway i got the hi-res screen and working nvidia drivers!

---

