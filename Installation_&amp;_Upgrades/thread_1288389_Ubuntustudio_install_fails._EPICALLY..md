---
title: "Ubuntustudio install fails. EPICALLY."
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by yoman82 on 2009-10-11
yoman82@yoman82-desktop:~$ sudo apt-get clean
yoman82@yoman82-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
yoman82@yoman82-desktop:~$ sudo apt-get install ubuntustudio-default-settings 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ubuntustudio-default-settings
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 6,608B of archives.
After this operation, 0B of additional disk space will be used.
0% [Connecting to us.archive.ubuntu.com]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe ubuntustudio-default-settings 0.26ubuntu1 [6,608B]
Fetched 6,608B in 7s (856B/s)                        
(Reading database ... 268110 files and directories currently installed.)
Preparing to replace ubuntustudio-default-settings 0.26 (using .../ubuntustudio-default-settings_0.26ubuntu1_all.deb) ...
Unpacking replacement ubuntustudio-default-settings ...
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
yoman82@yoman82-desktop:~$ sudo apt-get remove ubuntustudio-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ubuntustudio-icon-theme for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-default-settings for regex 'ubuntustudio-*'
Note, selecting usplash-theme-ubuntustudio for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-screensaver for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-artwork for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-desktop for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-video for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-audio-plugins for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-controls for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-gdm-theme for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-font-meta for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-theme for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-graphics for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-menu for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-sounds for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-audio for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-wallpapers for regex 'ubuntustudio-*'
Note, selecting ubuntustudio-look for regex 'ubuntustudio-*'
The following packages will be REMOVED:
  ubuntustudio-default-settings ubuntustudio-gdm-theme ubuntustudio-icon-theme
  ubuntustudio-look ubuntustudio-menu ubuntustudio-sounds ubuntustudio-theme
  ubuntustudio-wallpapers usplash-theme-ubuntustudio
0 upgraded, 0 newly installed, 9 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 35.3MB disk space will be freed.
Do you want to continue [Y/n]? ^C
yoman82@yoman82-desktop:~$ sudo apt-get remove ubuntustudio-de*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ubuntustudio-default-settings for regex 'ubuntustudio-de*'
Note, selecting ubuntustudio-desktop for regex 'ubuntustudio-de*'
The following packages were automatically installed and are no longer required:
  ubuntustudio-icon-theme ubuntustudio-theme ubuntustudio-sounds
  ubuntustudio-wallpapers ubuntustudio-look
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntustudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error processing ubuntustudio-default-settings (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntustudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
yoman82@yoman82-desktop:~$ 

I no longer can open synaptic, it gives me this error:
E: The package ubuntustudio-default-settings needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.



Help is greatly appreciated.

---

### Post by yoman82 on 2009-10-11
apt-get works, however update-manager crashes with the same problem as synaptic.

---

### Post by Intrepid Ibex on 2009-10-11
Please wrap that log in code tags ;) ([ code ]).

You could test this: ```
sudo rm /var/cache/apt/archives/ubuntustudio-default-settings* && sudo aptitude -f remove && sudo dpkg --configure -a
```

**E:** This will probably also prove to be helpful: [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

