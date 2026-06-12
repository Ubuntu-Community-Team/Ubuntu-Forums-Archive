---
title: "Hiding selected volumes on desktop"
date: 2008-11-01
forum: General Help
---

### Post by glotz on 2008-11-01
Hi there. I've been playing with funionfs (available in Hardy's universe) and it seems to work nicely. However my mount points end up displayed on my desktop and I don't like that. (However, I don't want to hide all volumes on desktop because that's the easiest way by far AFAIK to deal with usb sticks.)

This bug would seem to deal with the subject but I didn't manage to make it work. [https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886](https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886)

Could someone give it a try?

---

### Post by mojoman on 2008-11-01
> **glotz said:**
> Hi there. I've been playing with funionfs (available in Hardy's universe) and it seems to work nicely. However my mount points end up displayed on my desktop and I don't like that. (However, I don't want to hide all volumes on desktop because that's the easiest way by far AFAIK to deal with usb sticks.)

This bug would seem to deal with the subject but I didn't manage to make it work. [https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886](https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/34886)

Could someone give it a try?

Not sure what funionfs is but when I used a DE I didn't like that some partitions showed up on the desktop (I just wanted the USB-stick to show up, not, for example, the windows partition. I solved this by mounting them under /mnt instead of under /media. This probably varies between DE's but it might be worth a try (I used XFCE4 and I think it by default shows all partitions mounted under /media on the desktop).

/mojoman

---

### Post by glotz on 2008-11-01
Ah, nice, it works! Actually I had it mounted under my home folder in a random folder.

---

