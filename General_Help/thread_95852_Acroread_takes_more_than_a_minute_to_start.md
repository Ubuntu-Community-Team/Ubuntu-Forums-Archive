---
title: "Acroread takes more than a minute to start"
date: 2005-11-27
forum: General Help
---

### Post by asundaresan on 2005-11-27
hi,

when i load certain programs from the commandline like acroread, it takes more than a minute and freezes everything else. (i am not loading any file)

i notice that sometimes even gvim takes a few seconds to load. this just shouldn't take that much time. gimp sometimes takes a long time and hangs for some 10-20 seconds when opening a file. i used gentoo earlier on the machine and everything was quite fast.  

the system is dual processor xeon (pentium 2 GHz) with 1GB RAM and 2GB swap size. 

is there anyway i can find out why acroread is so damn slow and why certain programs like gvim or gimp take longer to start up?

thanks,
aravind.

---

### Post by mike_d on 2005-11-27
i hope some ubuntu guru's will respond to this.  i've also noticed things being much slower on my computers compared to when they ran gentoo.  to me it seems that disk access is slower (i do have hdparm enabled).   there's got to be a configuration option we're missing somewhere.

---

### Post by asundaresan on 2005-12-01
the problem is solved. it was a twisted solution. it was strange that my desktop, a much superior machine was having this problem, but my laptop wasn't. i noticed this problem in other gnome applications such as gimp, and eog too. the reason was my home was mounted as nfs and there were issues with file-locking and as a result the application didn't start. 

you get warnings like these

```
[aravinds@revathi ~]$ eog

** (eog:4193): WARNING **: Failed to lock:  No locks available

** (eog:4193): WARNING **: Failed to lock:  No locks available

```

the problem can be solve by installing and starting the **nfs-common** package which starts the portmap and nfs statd daemon.

```
root@revathi:/home/aravinds# apt-get install nfs-common
...
Setting up portmap (5-10ubuntu3) ...
 * Starting portmap daemon...                                                                                      [ ok ]

Setting up nfs-common (1.0.7-3ubuntu1) ...
 * Starting nfs statd...                                                                                           [ ok ]

```

---

