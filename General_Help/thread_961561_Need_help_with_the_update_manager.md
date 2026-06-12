---
title: "Need help with the update manager"
date: 2008-10-28
forum: General Help
---

### Post by nappymonster on 2008-10-28
Hi all,
I'm running a dual boot (gusty + vista, in about 10 minutes will upgrade to hardy), but due to various reasons I haven't used Ubuntu in a while - mostly because i've been needing the adobe CS4 collection and and office 07. I remember a while back for some reason or another I think I added some places that updates where downloaded from (the different source lists). I no longer want this, I want to official updates, but can't remember a thing about how to do this!

So, for gusty, how do i restore the default update settings. Should I update to hardy first then do this?

Cheers,
Nappymonster

---

### Post by TeoBigusGeekus on 2008-10-28
Do nothing - wait for a couple of days, then download Intrepid Ibex (Ubuntu 8.10) and do a clean install on your Ubuntu partition.

---

### Post by snowpine on 2008-10-28
The file /etc/apt/sources.list controls your software sources. You can edit it by opening a terminal and typing 'gksu gedit /etc/apt/sources.list' (without the quotes). The # character at the beginning of a line comments out that line, so just type a # at the beginning of any sources you don't want to use any more.

Whether to upgrade to Hardy or Intrepid is a completely separate question. :)

Good luck!

---

### Post by jerome1232 on 2008-10-28
To answer your question yes you can clean out your sources file. There's three ways really.

A)
```
gksu gedit /etc/apt/sources.list
# remove any entries in there that aren't official ubuntu sources
# now remove any other souce files, sources.list.d is a common directory to place another sources files.
sudo rm /etc/apt/sources.list.d/*
```

B)

This one is harder (involves know how to mount a disk and etc..)

boot from a live cd and mount your old root partition at /media/root, backup your old sources.list file, then copy the live cd's sources.list file on top of your old one. This is just an example you hardrive might be aranged differently so let us know if you need more assistance than this example.
```
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root
sudo cp /media/root/etc/apt/sources.list /media/root/etc/apt/sources.list.bck
sudo rm /media/root/etc/apt/sources.list.d/*
sudo cp /etc/apt/sources.list /media/root/etc/apt/sources.list
sudo umount /dev/sda1
sudo reboot
```

C) well it's not as good anyway and my fingers are tired of  typing :)

---

### Post by nappymonster on 2008-10-28
Thanks, but I had enough issues installing ubuntu the first time (gee I hate GRUB), so i'll leave it as it is. What I will at somepoint is disconnect the drive ubuntu is running on, then run supergrub to fix the mbr to just boot vista, then disconnect the internal one and plug in the external, and run it to just boot linux. That way I might finally be able to get a laptop that doesn't need the drive plugged in inorder to boot to anything. Thanks,
Nappymonster

---

### Post by nappymonster on 2008-10-28
Double post

---

