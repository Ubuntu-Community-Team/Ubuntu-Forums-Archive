---
title: "Problem removing some files (hidden, others)"
date: 2008-09-30
forum: General Help
---

### Post by coldfire204 on 2008-09-30
I installed wine from source on Ubuntu 8.04, and messed up part of the installation and wanna reinstall everything and start from scratch.  I was attempting to use wine to play Final Fantasy Online, and I think I know what I did wrong, but I want to remove all wine files, all configuration files, everything.  I used make install instead of checkinstall, btw.

First thing I did was go to my wine directory and sudo make uninstall wine, that worked okay.

Then I did rm -rf .wine - that was supposed to get rid of all hidden files but didn't exactly work as you can see in the following code, when I did locate wine:

What is the most efficient way of removing all this without messing up my installation?:confused: Thanks for any help anyone can give me for this.

```


bryandf@bryandf-desktop ~ $ locate wine
/etc/apt/sources.list.d/winehq.list
/home/bryandf/.wine
/home/bryandf/wine
/home/bryandf/wine-1.1.5.tar.bz2
/home/bryandf/.config/menus/applications-merged/wine-Programs-PlayOnline-PlayOnline Viewer.menu
/home/bryandf/.config/menus/applications-merged/wine-Programs-PlayOnline-Tetra Master.menu
/home/bryandf/.config/menus/applications-merged/wine-Programs-PlayOnline.menu
/home/bryandf/.local/share/applications/wine
/home/bryandf/.local/share/applications/wine-Programs-PlayOnline-PlayOnline Viewer-PlayOnline Viewer Config.desktop
/home/bryandf/.local/share/applications/wine-Programs-PlayOnline-Tetra Master-Tetra Master Config.desktop
/home/bryandf/.local/share/applications/wine.desktop
/home/bryandf/.local/share/applications/wine/Programs
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline/PlayOnline Viewer
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline/PlayOnline.desktop
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline/Tetra Master
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline/PlayOnline Viewer/PlayOnline Viewer Config.desktop
/home/bryandf/.local/share/applications/wine/Programs/PlayOnline/Tetra Master/Tetra Master Config.desktop
/home/bryandf/.local/share/desktop-directories/wine-Programs-PlayOnline-PlayOnline Viewer.directory
/home/bryandf/.local/share/desktop-directories/wine-Programs-PlayOnline-Tetra Master.directory
/home/bryandf/.local/share/desktop-directories/wine-Programs-PlayOnline.directory
/home/bryandf/.local/share/desktop-directories/wine-Programs.directory
/home/bryandf/.local/share/desktop-directories/wine-wine.directory
/usr/include/qt3/qwinexport.h
/usr/local/bin/wine
/usr/local/bin/wine-kthread
/usr/local/bin/wine-preloader
/usr/local/bin/wine-pthread
/usr/local/bin/wineboot
/usr/local/bin/winebrowser
/usr/local/bin/winebuild
/usr/local/bin/winecfg
/usr/local/bin/wineconsole
/usr/local/bin/winecpp
/usr/local/bin/winedbg
/usr/local/bin/winedump
/usr/local/bin/winefile
/usr/local/bin/wineg++
/usr/local/bin/winegcc
/usr/local/bin/winemaker
/usr/local/bin/winemine
/usr/local/bin/winepath
/usr/local/bin/wineprefixcreate
/usr/local/bin/wineserver
/usr/local/bin/wineshelllink
/usr/local/include/wine
/usr/local/lib/libwine.so
/usr/local/lib/libwine.so.1
/usr/local/lib/libwine.so.1.0
/usr/local/lib/wine
/usr/local/share/wine
/usr/local/share/applications/wine.desktop
/usr/local/share/man/de.UTF-8/man1/wine.1
/usr/local/share/man/fr.UTF-8/man1/wine.1
/usr/local/share/man/fr.UTF-8/man1/wineserver.1
/usr/local/share/man/man1/wine.1
/usr/local/share/man/man1/winebuild.1
/usr/local/share/man/man1/winedbg.1
/usr/local/share/man/man1/winedump.1
/usr/local/share/man/man1/wineg++.1
/usr/local/share/man/man1/winegcc.1
/usr/local/share/man/man1/winemaker.1
/usr/local/share/man/man1/wineprefixcreate.1
/usr/local/share/man/man1/wineserver.1
/usr/share/python-support/guidance-backends/wineread.py
/usr/share/python-support/guidance-backends/winewrite.py
/var/cache/apt/archives/wine_1.0.0-1ubuntu4~hardy1_i386.deb
/var/cache/apt/archives/wine_1.1.5~winehq0~ubuntu~8.04-0ubuntu1_i386.deb
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_Release
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_Release.gpg
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_binary-i386_Packages
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/wineread.pyc
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/winewrite.pyc


```

---

### Post by kpkeerthi on 2008-09-30
The locate database needs to be updated to reflect the changes.
```

sudo updatedb
locate wine

```

---

### Post by coldfire204 on 2008-09-30
I went down the list and deleted as many of those files as I could, but it wouldn't let me have access to all of them, so I tried changing the file permissions, still no luck.  

Another weird thing, the files that I did manage to delete still show up when I do locate wine in terminal, even after a restart.  :confused:

---

### Post by justleen on 2008-09-30
most of what the locate finds doenst matter, you should be able to reinstall fine. 

If you really want to remove everything, you'd have to do a find on the several folder found, and -exec rm the files.

```

cd /usr/local/
find . -name *wine* -exec rm {} \; 
```

you could use the output of the locate, but that will delete the source files as well.
```

for FILES in `locate wine`; do rm $FILES; done 
```

---

### Post by coldfire204 on 2008-09-30
Thanks kpkeerthi, that command updated the locate list with everything I went through and deleted:)

Justleen, I'll give that a shot, I'd really like to just go ahead and reinstall and try again, but winehq insists that every single last wine file on the system be deleted before recompiling or it'll cause all sorts of catastrophic problems :(

---

