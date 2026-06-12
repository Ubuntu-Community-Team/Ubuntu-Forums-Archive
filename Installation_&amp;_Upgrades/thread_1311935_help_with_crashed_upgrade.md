---
title: "help with crashed upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by cmgaviao on 2009-11-02
Ok,  Im pretty much a noob where ubuntu is concerned....After happily running along for the past 6 months or so, i decided to do the upgrade.

halfway through, i had to step out and I guess my anemic battery decided to step out too...

Now, when I try to boot, I get the following message:

mountall: symbol lookup error:  mountall:  undefined symbol:  udev_monitor_filters_add_match_subsystem_devtype 

init:  mountall main process (792) terminated with status 127

I've tried booting to the other kernels in grub and they all give me the same message in the end.

my drive is intact and I can retrieve all my files if i were to reinstall...though the nightmare of getting citrix and virtualbox working again make this option not very desirable.

TIA for any ideas.


cmg

---

### Post by antiram on 2009-11-02
you could use a chroot for further install/repair.
boot from karmic (or other ubuntu, debian) livecd
if your dead install is on sdX:

sudo mount /dev/sdaX /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt /bin/bash

your root filessystem is now the dead installation.
"apt-get update" and "apt-get dist-upgrade" should work now

---

### Post by cmgaviao on 2009-11-02
ok thanks a bunch....i now boot straight into a shell... how can i get it to boot to the desktop?

---

### Post by Ptero-4 on 2009-11-03
> **cmgaviao said:**
> ok thanks a bunch....i now boot straight into a shell... how can i get it to boot to the desktop?
You need to do the
```

apt-get update

```
and
```

apt-get dist-upgrade

```
to complete the unfinished upgrade process. Then it will boot your HD installation to the desktop.

---

### Post by hariks0 on 2009-11-03
I upgraded using alternate cd. There was a error message and warning [that the system may be unusable] at the end of upgrade. I can now boot to Karmic but the mouse cursor is nowhere to be seen after I login. I can use the mouse by guessing its location. The desktop displays some static colors as it does in low resolution.I had created two aptoncd image before and after the upgrade.

Now my questions are:-

1. Is it possible to complete the upgrade and get the system back to normal Karmic ?

2. Can I restore all my installed applications from either of the aptoncd images ?

---

### Post by sikosis on 2009-11-03
Tried all those ... no success.

---

### Post by sikosis on 2009-11-03
Actually turned out there was no DNS in Terminal.

I had to edit my /etc/resolv.conf  and add the search domain and nameserver(s).

search domain.com
nameserver <IP_ADDRESS>


It now appears to be doing an update and upgrade. Fingers crossed.

---

### Post by cmgaviao on 2009-11-03
> **Ptero-4 said:**
> You need to do the
```

apt-get update

```
and
```

apt-get dist-upgrade

```
to complete the unfinished upgrade process. Then it will boot your HD installation to the desktop.
 
 
I had actually done those....Did them again just to be sure and the same thing...
 
BUT strangely enough, I fell asleep with it logged in to the shell and the battery died.  Woke up this morning turned it on and it booted straight to the desktop.... Go figure????  The strange thing, it didnt update the taskbar icons to the new ones and also didnt seem to install the new chat client (cant think of the name of it now).  It may have not installed other items, but those are the two that are standing out right now.  No biggie, as I'm thrilled to have the rest of my stuff working without having to do a fresh reinstall.!
 
Thanks a million for all the help.

---

