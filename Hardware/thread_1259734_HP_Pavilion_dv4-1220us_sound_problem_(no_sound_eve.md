---
title: "HP Pavilion dv4-1220us sound problem (no sound even with headphones)"
date: 2009-09-06
forum: Hardware
---

### Post by sd.gas on 2009-09-06
Hi everyone, i'm kind of noob in this linux enviroment, i installed it and i got no sound, i've been reading and trying a lot of things and none work, and then i tried using my headphones, and even with headphones i can't hear anything, idk what to do now T.T (was working a couple of hours ago on windows 7)

i'm on Ubuntu 9.04 64-bit and my pc specs are:

2.0 GHz AMD Turion x2 RM-72 processor
4GB RAM
250 Hard Drive

---

### Post by JC Cheloven on 2009-09-06
First of all, have you checked that the volume sliders are not muted? Please cllick on the little speaker on the upper panel, go to volume control, and see what is over there. Also check what device is selected (at the top of that window).

Alternatively, yo can ckeck almost the same opening a terminal and typing ```
sudo alsamixer
```

Please come back to tell us what you see. If the problem isn't solved, there sould be a sound card problem that we could investigate.

---

### Post by sd.gas on 2009-09-07
yeah, actually, it's full and nothing can be heard =/

---

### Post by Tyorik on 2009-09-07
I have the same problem with an HP dv4-1120us. On top of no sound, I also get these while trying to FIX the no sound problem:

[quote=]petsche@Optimus:~$ sudo alsamixer
[sudo] password for petsche: 

alsamixer: function snd_ctl_open failed for default: No such file or directory
petsche@Optimus:~$ [/quote]

When I try an apt-get:

[quote=]petsche@Optimus:~$ sudo apt-get install gnome-alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-alsamixer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.7kB of archives.
After this operation, 602kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gnome-alsamixer
Install these packages without verification [y/N]? y
Err [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) jaunty/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2
  500 Internal Server Error
Failed to fetch [http://kr.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb]("http://kr.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7%7Ecvs.20060916.ds.1-2_i386.deb")  500 Internal Server Error
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
petsche@Optimus:~$ [/quote]

I'm on 9.04 Jaunty, by the way...

Still no sound though... :(

---

