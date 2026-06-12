---
title: "sound problem :'("
date: 2010-12-23
forum: Hardware
---

### Post by m3asmi on 2010-12-23
hello !

I have a very bad problem with my ubuntu because I can't play any** sound** now 

```
rachid@netbook:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/rachid/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/rachid/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

```
rachid@netbook:~$ alsamixer 
cannot open mixer:*No file or folder of this type*
```

can you help me please  ^_^

---

### Post by m3asmi on 2010-12-23
no reply !!!!!

---

### Post by rlmill on 2011-01-08
I have the exact same problem. Originally, I had working sound but my internal mic wasn't picking up. So I followed the advice on this guide:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

and now I have no sound at all. No devices even show up. I've tried compiling and installing newer ALSA versions from their website, to no avail. I know the card is fine, as other operating systems on the same machine have no problem.

---

