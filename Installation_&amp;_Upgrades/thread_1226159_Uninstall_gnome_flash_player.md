---
title: "Uninstall gnome flash player"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by ki4jgt on 2009-07-29
I installed gnome flash player, but it's slowing down my machine. So I was wanting to install adobe, when I use synaptic, it gives me an error message, after trying to completely remove swf for mozilla.

---

### Post by wojox on 2009-07-29
```
sudo apt-get remove swfdec-mozilla
```

---

### Post by Sef on 2009-07-29
Remove it with Add/Remove or synaptic if that is how you installed it.

---

### Post by ki4jgt on 2009-07-29
tried sudo, All I get is an error message. I'm using 9.10.

---

### Post by wojox on 2009-07-29
What's the error message?

---

### Post by ki4jgt on 2009-07-29
sudo apt-get remove --purge swfdec-mozilla
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtwolame0 gstreamer0.10-plugins-ugly linux-headers-2.6.31-3 linux-headers-2.6.31-3-generic libswfdec-0.8-0 libsidplay1
  libmad0 libid3tag0 libmpeg2-4 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  swfdec-mozilla*
0 upgraded, 0 newly installed, 1 to remove and 44 not upgraded.
After this operation, 303kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132060 files and directories currently installed.)
Removing swfdec-mozilla ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing swfdec-mozilla (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 swfdec-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kjasontu on 2009-11-10
I also installed the gnome version of Flash and shockwave player in Firefox and it is terrible.  I want to uninstall and use Adobe instead, but I can't find it in Firefox's extensions or in Add/Remove programs.  I am an Ubuntu noob so don't assume I know anything. :P

I am also using 9.10.

---

### Post by Kjasontu on 2009-11-10
> **wojox said:**
> ```
sudo apt-get remove swfdec-mozilla
```

This worked for me.

ki4jgt, did you close your browser first?

---

