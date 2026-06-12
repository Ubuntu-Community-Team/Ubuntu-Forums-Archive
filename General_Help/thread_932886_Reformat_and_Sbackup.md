---
title: "Reformat and Sbackup"
date: 2008-09-28
forum: General Help
---

### Post by I[AM]SMRT on 2008-09-28
Well after a load of unexpected problems, trying to restore with sbackup (which only made everything worse), I decided to just do a fresh install of Ubuntu.

Anyways, I ran sbackup to restore a few directories and now it seems I've got some problems/conflicts with programs I'm trying to run:

```
brian@brian-laptop:~$ mplayer
mplayer: error while loading shared libraries: libXvMC.so.1: cannot open shared object file: No such file or directory
brian@brian-laptop:~$ texmaker
texmaker: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
brian@brian-laptop:~$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: No module named compizconfig

```

Any suggestions so that I can run these programs? I've tried uninstalling/reinstalling but nothing.

I may just do a fresh install of Ubuntu again and forget about the backup I made with sbackup (it's only ~5 gb and the file system I put it on isn't VFAT/FAT32, so idk what's up with that). What are some good backup options? 

Thanks,
SMRT

---

