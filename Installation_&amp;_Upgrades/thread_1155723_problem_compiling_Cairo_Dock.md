---
title: "problem compiling Cairo Dock"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by ewout on 2009-05-11
Since my latest reinstall of ubuntu 9.04 compiling Cairo Dock doesn't work anymore. After entering the command 'make' a few moments later it starts an endless loop stating:

      && CONFIG_FILES=po/Makefile.in CONFIG_HEADERS= CONFIG_LINKS= \
           /bin/sh ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
make[2]: Leaving directory `/home/ewout/Downloads/cairo-dock-2.0.0-rc5/po'
make[2]: Entering directory `/home/ewout/Downloads/cairo-dock-2.0.0-rc5/po'
cd .. \
      && CONFIG_FILES=po/Makefile.in CONFIG_HEADERS= CONFIG_LINKS= \
           /bin/sh ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
make[2]: Leaving directory `/home/ewout/Downloads/cairo-dock-2.0.0-rc5/po'
make[2]: Entering directory `/home/ewout/Downloads/cairo-dock-2.0.0-rc5/po'
cd .. \

and so forth. It keeps repeating these lines. Before my reinstall of 9.04 I used a normal ext3 filesystem with no advanced stuff whatsoever and Cairo Dock worked perfectly. Then I tried a crypto LVM ext3 and no luck, compiling didn't work. Just LVM and ext3 again no. LVM and ext4 no luck again. I also tried using automake 1.9 instead of automake 1.10 but that didn't work either. Any help would be welcome. I'm a bit out of fresh ideas, especially because I had Cairo Dock up and running (and enjoying) until a few days ago.

---

### Post by ewout on 2009-05-11
Anybody?

---

### Post by Partyboi2 on 2009-05-11
Hi, have you tried installing the version in the ubuntu repos? You can do that by opening a terminal and typing
```
sudo apt-get install cairo-dock
```
If you want a later version (2.0) You can go [[COLOR=Blue]here[/COLOR]]("http://developer.berlios.de/project/showfiles.php?group_id=8724") and download the deb package and once downloaded double click the downloaded deb to start the install process.

---

