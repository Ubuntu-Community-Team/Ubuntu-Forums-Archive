---
title: "NVidia - Problem with 6200 / 6600: screen get jumbled"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by fdimeglio on 2005-05-07
Hi,

I am posting here this problem which was also reported previously on [http://ubuntuforums.org/showthread.php?t=31015](http://ubuntuforums.org/showthread.php?t=31015). I think that it is more a hardware related problem.

Description: after use of FireFox (mainly) the screen get jumbled (see photos: [http://ubuntuforums.org/showthread.php?t=31015](http://ubuntuforums.org/showthread.php?t=31015))

I have exactly the same problem with both Ubuntu 5.04 in x86 and amd64. 
BTW it works perfectly with Windowz.

My configuration is:

- Shuttle SN25P
- AMD64 3200+ 90nm
- 2*512 RAM (Corsair PC 3200 Value Edition)
- Leadtek WinFast PX6200 TC TDH 128M
- LCD LG 1720P
- resolution 1280*1024 at 60Hz

It seems that this problem comes when using FireFox and especially when browsing on pages where there are some animated gifs.

I was wondering if this does not come with Turbo Cache but the other post shows that with a NVidia 6600 GPU the problem is the same. Please note that this problem has been related on both Leadtek cardswith NVidia 6xxx GPU.

I will test it with lower resolutions.

Any clues / help ?

Thank you.

Fabrice

---

### Post by fdimeglio on 2005-05-08
Changing resolution does not fix the problem

---

### Post by fdimeglio on 2005-05-08
OK, after numerous tries and search on the forum, the fix was to install NVidia driver and enable it.

Look at: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

It may be a mess (eg to a search on "nvidia" in the Ubuntu forum) but worked so far for me  ](*,) 

Good luck

Fabrice

PS: btw the Xorg driver "nv" (and not "nvidia" which is the Nvidia proprietary one's) seems to be buggy ...

---

### Post by voidlogic on 2005-06-06
Installing the nVidia driver is a breeze. I read that the latest driver fixes 6200 issues. Use the package manager to download all the headers for your kernel. Then reboot, go in recovery mode. At the command prompt you need to run a command, modprobe -m (i think, google that) and then execute the nVidia installer. Before you go through all that work, make sure the nvidia driver in the package manager isn't the latest, becuase thats VERY simple too install. Mark for insallation, install, run the command in the packages comment feild to enable it. good luck.

---

