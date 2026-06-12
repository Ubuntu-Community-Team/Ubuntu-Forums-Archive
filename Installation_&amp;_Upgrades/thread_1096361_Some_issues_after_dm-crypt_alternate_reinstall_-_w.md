---
title: "Some issues after dm-crypt alternate reinstall - wireless, sound, etc."
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by FiberOptix on 2009-03-14
Hey all,

Following the advice given in some of the threads on this forum, I tar'd up the contents of most of my hard drive:

tar cvpzf backup.tgz --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

Booted into the alternate installer and proceeded with reinstalling into a new encrypted lvm setup. After this was finished, I copied /etc/fstab, /etc/crypttab, and /boot, then extracted everything from backup.tgz, then restored /etc/fstab, /etc/crypttab, and /boot from the copies that I'd made.

I've encountered some issues and remain skeptical that I'm in the clear. The first thing I'd like to resolve is my internet access. I'm using my wireless interface to connect and despite the fact that I can see the interface come up and exchange packets  with the AC, for some reason the connection manager nolonger runs (or appears on my toolbar) on boot and so I'm without internet. Second is sound, it's the same sort of issue as I can hear the song and dance from when gnome starts but then when I access the volume control on my toolbar I get an error message saying that the device wasn't found.

I would really appreciate any help.

---

### Post by FiberOptix on 2009-03-15
/bump

---

### Post by FiberOptix on 2009-03-15
Beuller... Beuller...

So from scratching my head and not being able to come up with anything I've reinstalled ... again... And will be replacing select components (like /home) from my backup, and will have to spend some time reconfiguring and installing packages to try to get it running like the well oiled machine it was before, sadly.

I'm still looking for bright ideas as I still have the backup and would like a quick way of restoring.

Anybody?

---

