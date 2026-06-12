---
title: "nvidia failure after reboot--fixed"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by marx1984 on 2005-10-11
I have a nVidia riva TNT2 M64 card on my system. I upgraded my kernel to 2.6.11 to support v4l for my camera and the nVidia drivers provided by apt repositories stopped working. So I then decided to reinstall nVidia-glx to see if things would somehow fix, but it did not. So I uninstalled nvidia-glx and nvidia-settings. Then I tried nVidia 7174 OEM drivers which were terribly buggy with my 2.6.11 kernel. After many searches, I found an article stating that the nVidia drivers(from nVidia) may be unstable when used with certain kernels, such symptoms included freezing of X or gnome when running firefox, as it was during my expirience, and also sometimes rendering the system completely inoperable with some kernels that utilize a certain ?caching? function. So I reverted back to a 2.6.10 series kernel and configured it(custom not original ubuntu kernel) and downloaded the 7174 drivers from nVidia (note some versions of the driver will not work with your GPU depending on how old you card is). I did that because nVidia-glx would not operate correctly on my custom kernels. I installed the nVidia OEM drivers, edited xorg.conf, and ran sudo /etc/init.d/gdm restart. It worked, but after every reboot X would fail and I would have to recompile and reinstall the nVidia OEM drivers and restart GDM to get X working. I tried to reasure myself nvidia-glx and nVidia-settings were uninstalled and to my surprise nvidia-settings was on the system after apt reported otherwise. I manually remove it. I checked /etc/init.d/ and saw that an nvidia-glx script was there and executable, so I ran chmod -x nvidia-glx in the /etc/init.d/ dir to disable it, checked my /etc/rc2.d and saw that nvidia-glx was being run everytime the system booted(my first thought was this is the cause of the failure of X when trying to load the nvidia driver after every reboot!). And behold that was the cause of the problem, the nvidia-glx script was being run even though kerneld was initializing the nvidia OEM driver. So that's why X wouldn't start properly after reboots, I'm guessing there was a conflict. Now my system runs fine and i have no segmentation faults when running xmms, mplayer, and glxgears. 

What led me to think that something was conflicting with the nvidia driver was nvidia's own install problem. It reported that the driver was somehow altered since the last install.

Note: When I ran the lsmod utility after X's failure, it would report that the nvidia driver was loaded. and after rmmod nvidia and /etc/init.d/gdm restart nvidia would load but X wouldn't funtion at all. I do not know why.

good luck, I hope this helps some of you. Sorry for the poor structure of this post. Any feedback is welcome.

---

