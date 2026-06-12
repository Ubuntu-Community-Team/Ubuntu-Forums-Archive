---
title: "New motherboard, video problems."
date: 2013-06-07
forum: Hardware
---

### Post by cackerso on 2013-06-07
I recently had to replace my motherboard.  I was having some intermittent video problems so I decided to go back to the recommended Nvidia driver 304 rather than the 310 I was using. I used the driver update app from the system menu. After it was done I rebooted as recommended. After an initial Kubuntu screen, at the point it goes to the login screen, it goes black and I get a login command prompt.

If I try "startx" I get a lot of output but the core problem seemed to be this: 

"Using '/usr/share/x11/xorg.conf.d NVIDIA API mismatch. Kernel module has version 310 but this NVIDIA driver component has version 304. Please make sure that the Kernel module and the NVIDIA driver component have the same version."

I'm running kernel version 3.2.0-45-generic.  Then I followed advice in another post and did the following:

1. sudo rmmod nvidia
2. sudo apt-get purge nvidia-current 
3. sudo apt-get purge  nvidia-current-updates
4. sudo rm /etc/X11/xorg.conf
5. sudo dpkg-reconfigure xserver-xorg

and I got my desktop back. The weird part is that I don't seem to be running the Nouveau driver, I seem to be back to Nvidia 310. How do I check what driver is really the installed one? How do I check that everything is ok with the system so I don't have the same problem in the future if I try to change the driver?

---

