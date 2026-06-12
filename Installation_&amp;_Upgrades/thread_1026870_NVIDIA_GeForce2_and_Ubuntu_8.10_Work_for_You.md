---
title: "NVIDIA GeForce2 and Ubuntu 8.10 Work for You?"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by waltkerr on 2008-12-31
Has anyone successfully installed Ubuntu 8.10 on a PC with an NVIDIA GeForce2 integrated graphics chip? I can't get mine to work. I've tried activating the driver through System|Administration|Hardware Drivers  process, tried envyng, tried NVIDIA drivers 96.43.07, 96.43.09 and 71.86.04 and the result is either a black screen and hang at bootup or glitches and crashes after bootup into Gnome. I've tried every suggestion on every forum I can find and nothing works. Now shopping for a new graphics card because I love Ubuntu! Just curious.
.

---

### Post by 67GTA on 2008-12-31
The 71 and 96 series 3D drivers are not compatible with 8.10's xorg version. You will have to use the opensource nv driver. 8.04 still works with the legacy drivers. More info on release notes page: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by PsYcHoTiC_MaDmAn on 2009-01-01
I've had the smaqe problems, downloaded 8.04 to try and compensate for that, and the sodding thing wont install(either from a disk or USB (via unetbootin))

are there any other work arounds for it?? basically all mI want it for is to increase the screen resolution, the maximum that old CRT monitor will support is 1153/876 but ubuntu will only go as far as 800/600, though I know the the nForce 2 chipset will support 1024/768 (ran xp of the other disk at that resolution) 

why does the 96 drivers carry the recommended bit then if its incompatible..

---

### Post by waltkerr on 2009-01-01
I also tried the 173 driver as Nvidia's information seemed to indicate it might be the one. But got the same result. The system does run, sliggishly, and I can set the resolution as high as my LCD supports, but some menus don't paint correctly; menu items don't show up until you move the pointer over them. Mostly Firefox crashes sooner or later as well. I really want to get rid of XP totally and go fully Ubuntu on this machine. I'm now lookng at a new graphics card, something not too expensive which has a more current chip that is supported by the new drivers.

---

