---
title: "how to install ubuntu in separete partition"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by saka on 2009-04-28
I'm using ubuntu 8.10 installed inside windows Vista and I'd like to move it to a separete partition is there any way to do that with out loosing my settings and files and updates

---

### Post by LIB53 on 2009-04-28
I doubt it. The best you could do is go to your home folder and press ctrl+H to show hidden files and back up your configurations which are found in these hidden folders. When you install Ubuntu 8.10 like normal (separate partition), just copy and paste in your configuration files. You should also note your software sources and applications you installed.

I did find some stuff when i googled "moving from wubi", but they seemed to be for Ubuntu 8.04, or some portable edition. I still think you should check out these articles. Sorry for not being much help, but i thought i might give you what help i could.

---

### Post by Partyboi2 on 2009-04-28
Hi, you can use LVPM to migrate your wubi install to its own dedicated partition. See [[COLOR=Blue]here[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by Mark Phelps on 2009-04-28
While it CAN be done, you will need an area of unallocated space to which to migrate the Ubuntu installation.  If you don't have that space and will need to shrink Vista to make if available, maker sure that you have a Vista DVD, and are prepared to boot with it to do Startup Repair (if needed), since GPArted has been known to corrupt Vista partitions sometimes.

Also, if you have only one partition on only one drive, and that is Vista, you will have additional problems because Ubuntu is already installed inside that partition -- which may prevent you from shrinking it enough to get the room you need.

Given these limitations, you may find that the back-off data, resize, and install from scratch approach may be the best one.

---

