---
title: "Thinkpad ultranav in Lucid Lynx"
date: 2010-04-29
forum: Hardware
---

### Post by jervlet on 2010-04-29
Hi everybody, I've made a clean install of ubuntu 10.04 lucid LTS. My problem is that I can't make ultranav to work on my ThinkPad T60. Solutions I've found are either based on configuring Xorg-Server files or HAL. But since ubuntu is not using neither of those anymore, I was wondering if anyone found a solution how to enable ultranav functionality.

gpointing-device-settings utility is not working for me either :(

Any ideas?
Thanks in advance!*[I]*[/I]

---

### Post by DomesDKG on 2010-04-30
I'm having the same problem, all the old solutions don't work in 10.4.  Any suggestions would be appreciated!

---

### Post by peepingtom on 2010-05-01
Grab gpointing device settings from Debian, they have version 1.5.1 and it retains the settings.

[https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754)

How is it not working?

---

### Post by DomesDKG on 2010-05-01
Sorry for my inexperience, but could you explain how to install 1.5.1 on Lucid?

---

### Post by DomesDKG on 2010-05-02
Ok, you can get the download files for 1.5.1 from here:
[http://packages.debian.org/sid/libgpds0](http://packages.debian.org/sid/libgpds0)
[http://packages.debian.org/sid/gpointing-device-settings](http://packages.debian.org/sid/gpointing-device-settings)
I'm not sure if you need this third one, but I installed it.
[http://packages.debian.org/sid/libgpds-dbg](http://packages.debian.org/sid/libgpds-dbg)
Afterwards you can configure it in system>preferences>pointing devices.  I set it to use wheel emulation, and button 2 to get it to work.

---

### Post by jervlet on 2010-05-04
DomesDKG, that worked out well.

First time I simply forgot to set "wheel emulation button" to '2' (was set to '4' for me).

Thanks!

---

### Post by joechiang on 2010-05-23
> **DomesDKG said:**
> Ok, you can get the download files for 1.5.1 from here:
[http://packages.debian.org/sid/libgpds0](http://packages.debian.org/sid/libgpds0)
[http://packages.debian.org/sid/gpointing-device-settings](http://packages.debian.org/sid/gpointing-device-settings)
I'm not sure if you need this third one, but I installed it.
[http://packages.debian.org/sid/libgpds-dbg](http://packages.debian.org/sid/libgpds-dbg)
Afterwards you can configure it in system>preferences>pointing devices.  I set it to use wheel emulation, and button 2 to get it to work.

just login to say thanks DomesDKG, it worked well for me for my T500 :D

---

