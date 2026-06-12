---
title: "ubuntu`s slowing down?"
date: 2005-12-02
forum: General Help
---

### Post by kxs on 2005-12-02
Hi, I`ve noticed lately that mplayer starts quite a long time. Even if the movie file I want to run is less then 50 megabytes. Did anyone have this problem?
Also, when I copy files from CD to hdd, Gnome becomes very slow. I can`t even move the mouse cursor smoothly :???:

---

### Post by sigma2805 on 2005-12-02
i've noticed that if my home drive is filled up and there is very little or no space on there my computer slows down as well...

---

### Post by anil_robo on 2005-12-03
I am not an expert, but I think using a swap partition can prevent slowing down when there's low disk space. I use 1GB swap partition always.

---

### Post by kxs on 2005-12-03
Well, I don`t know if this is causing the problem. I`ve got over 4 GB of free disk space. It`s not much, but not little either. I don`t have to much swap, just 256 MB, but there is quite a lot of RAM - 640 MB, so I thing it`s enough.
Maybe I messed up something adding these lines to xorg.conf:
```
	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "COMPOSITE"
	Option "TVStandard" "PAL-G"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
```
I`ve noticed that since than my computer hangs when my monitor`s off and screensaver turns on. :???:

---

### Post by Ozric Tentacle on 2008-01-26
Run it from gnome-terminal, I think it's related to the script disabling the screensaver. Does it pause for like 5-6 seconds before playing? Run in shell ("mplayer nameofmovie") and try ctrl+c when it pauses.

---

