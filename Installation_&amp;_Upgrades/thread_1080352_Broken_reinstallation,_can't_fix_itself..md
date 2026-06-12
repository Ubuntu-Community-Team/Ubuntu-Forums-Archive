---
title: "Broken reinstallation, can't fix itself."
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by njd4k on 2009-02-25
I switched this week from a dual boot system to 100% Ubuntu (yay!), but in the process of reshuffling partitions, wound up reinstalling Intrepid from scratch. Fortunately, I had backed up my system... but unfortunately, SBackup seems to freeze up if I reinstall a directory with any large files in it. After hours of installing one set of preferences after another, I gave up.

So now I have a system that's partly restored, and partly fresh. What I would like to do is keep the settings I've been able to repair, while reinstalling anything that isn't quite right. Unfortunately, I can't seem to get any package management to work because my Google Desktop installation is broken. When I try to install from the .deb file, the package manager crashes; Synaptic automatically closes when I try to open it; apt-get and dpkg won't reinstall or remove the program, because it can't see the .deb file and not all the files that should be there, are. This happens even when I try using force options for dpkg and apt-get.

I have Google's .deb file, and most of the error messages boil down to some variation on "I can't reinstall this without an archive." Is there some way to tell apt-get where it is? Is there some directory where it will be automatically detected? Or am I going to have to reinstall from the CD and just do it all over again?

---

### Post by njd4k on 2009-02-25
Examples:
```

nic@nic-laptop:/opt/google/desktop$ sudo apt-get remove google-desktop-linux --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it.
```
```

nic@nic-laptop:/opt/google/desktop$ sudo dpkg -r --force-remove-reinstreq google-desktop-linux
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 194350 files and directories currently installed.)
Removing google-desktop-linux ...
PREFIX is differ than recorded ROOT_DIR!
dpkg: error processing google-desktop-linux (--remove):
 subprocess pre-removal script returned error exit status 1
File /opt/google/desktop/bin/install_firefox_plugin.sh is missing!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 google-desktop-linux
```

---

### Post by njd4k on 2009-02-25
I think the problem was that I originally installed google desktop from google's repositories. I gave up and reinstalled everything again. So much for my high scores in the robot game.

---

