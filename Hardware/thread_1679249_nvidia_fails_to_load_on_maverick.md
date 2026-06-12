---
title: "nvidia fails to load on maverick"
date: 2011-01-31
forum: Hardware
---

### Post by pickarooney on 2011-01-31
Since updating my old laptop to Maverick I can't get any nvidia drivers to work.
I upgraded via apt-get distro upgrade and lost my GUI, basically.
When I run jockey, it tells me there is one driver version available - 96
However, on restarting with the nvidia driver enabled I get an error message "unable to load module nvidia"
I can run a GUI by creating an xorg.conf and changing the driver to the basic nv one.

What do I need to do to get some (any) version of the nvidia driver to work with this card?

---

### Post by cascade9 on 2011-02-01
Its still failing? Tsk tsk canonical, the newer version of the 96.xx drivers that works with the xorg version in 10.10 has been out for months now. 

There are 2 ways should be able to fix this, either manually install the newest 96.xx drivers, or use a PPA. See here (post #9)- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10068387](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10068387)

---

### Post by pickarooney on 2011-02-01
Perfect, thanks!

Ubuntuforums 1 - 0 Canonical

---

### Post by cascade9 on 2011-02-02
Cool, fixed. 

BTW, its a god idea to mark threads with solution with the 'solved' tag (in thread tools).

---

### Post by pickarooney on 2011-03-13
I have to reopen this unfortunately as it's stopped working again. I guess some update screwed up my gfx drivers again and this time the PPA is not helping. Incidentally on the PPA page it describes itself as obsolete due to Maverick including the latest driver. I tried installing the drivers directly from nvidia's website but although the installer ran without errors I still can't get any display. It seems as though the official latest drivers (96.43.19) don't actually work any more!

I've no idea where to go with this apart from using the crappy nv drivers.

---

