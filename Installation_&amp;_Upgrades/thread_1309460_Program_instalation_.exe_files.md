---
title: "Program instalation .exe files"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Marilen on 2009-11-01
Hi, I'm new to Ubuntu (a week) I currently want to install programs into the computer for example: blackberry software, itunes, winrar, etc and for some reason when i try opening the executable files this shows up: :(

Archive:  /home/marilen/Downloads/wrar390.exe
[/home/marilen/Downloads/wrar390.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/marilen/Downloads/wrar390.exe or /home/marilen/Downloads/wrar390.exe.zip, and cannot find /home/marilen/Downloads/wrar390.exe.ZIP, period.

I would like to know if there is anything i can do, or what's going on...

Thank you so much 

Marilen N. Costarelli :D

---

### Post by macogw on 2009-11-01
.exe are Windows programs.  They're for Windows, not Linux.  You can try installing them through WINE (which you'll need to install first from the Software Center or Applications -> Add/Remove depending on which version of Ubuntu you use), but I can tell you right now that the newest version of iTunes you'll have any luck with is 6.  I think there's some Free Software capable of talking to Blackberries.  And there is definitely an "unrar" program available in the repositories.

---

### Post by llamabr on 2009-11-01
You should visit, and ask questions like this, on the absolute beginner forum, not the installation forum.  But look here:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by matthewbpt on 2009-11-01
The programs you are trying to install are Windows programs, not Linux programs. You can install wine, a windows compatibility layer for Linux, but I think you'll be much better off finding equivalent native linux programs, they are ussually better than their windows counterparts anyway. For itunes I recomend you try Rhythmbox, Banshee or Amarok. To use rar files you can install the unrar package. I don't know about the blackberry software though.

Remember windows executables (.exe) are not linux executables,

---

### Post by Soul-Sing on 2009-11-01
Try always first native linux progs, maybe this will be heplful: [http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by llamabr on 2009-11-01
Wine is almost never the correct solution.  Here's some blackberry apps:

```
brock@hops:~$ apt-cache search blackberry
barry-util - Command line utilities for working with the RIM BlackBerry Handheld
barry-util-dbg - Command line utilities for working with the RIM BlackBerry Handheld
barrybackup-gui - GTK+ based GUI for backing up the RIM BlackBerry Handheld
barrybackup-gui-dbg - GTK+ based GUI for backing up the RIM BlackBerry Handheld
libbarry-dev - Development files for libbarry
libbarry0 - Library for using the BlackBerry handheld on Linux
libbarry0-dbg - Library for using the BlackBerry handheld on Linux
opensync-plugin-barry - Opensync Blackberry plugin, based on the Barry project
opensync-plugin-barry-dbg - Opensync Blackberry plugin, based on the Barry project
brock@hops:~$ 

```

---

