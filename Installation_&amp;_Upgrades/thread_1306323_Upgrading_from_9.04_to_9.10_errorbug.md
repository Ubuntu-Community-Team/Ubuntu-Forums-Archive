---
title: "Upgrading from 9.04 to 9.10 error/bug"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Shamsul007 on 2009-10-30
_[IMG]http://img408.imageshack.us/img408/7672/screenshot1hm.png[/IMG]_

any idea what this means?. i just went to upgrade thing and i clicked to upgrade to 9.10

these are the log files

apt.log
> Log time: 2009-10-30 16:15:19.080528
Log time: 2009-10-30 16:15:23.752624
Log time: 2009-10-30 16:15:52.592310
Log time: 2009-10-30 16:16:26.517233

main.log
> 2009-10-30 16:15:14,676 INFO Using config files '['./DistUpgrade.cfg']'
2009-10-30 16:15:14,761 INFO release-upgrader version '0.126.6' started
2009-10-30 16:15:15,131 DEBUG svg pixbuf loader failed (Error displaying image)
2009-10-30 16:15:15,134 DEBUG Using 'DistUpgradeViewGtk' view
2009-10-30 16:15:15,177 DEBUG aufsOptionsAndEnvironmentSetup()
2009-10-30 16:15:15,177 DEBUG using '/tmp/upgrade-rw-4INSL6' as aufs_rw_dir
2009-10-30 16:15:15,178 DEBUG using '/tmp/upgrade-chroot-lAhc5X' as aufs chroot dir
2009-10-30 16:15:15,178 DEBUG enable dpkg --force-overwrite
2009-10-30 16:15:15,261 DEBUG lsb-release: 'jaunty'
2009-10-30 16:15:15,281 DEBUG who -m --ips: ''
2009-10-30 16:15:15,282 DEBUG _pythonSymlinkCheck run
2009-10-30 16:15:15,319 DEBUG openCache()
2009-10-30 16:15:19,086 DEBUG /openCache(), new cache size 26966
2009-10-30 16:15:19,086 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2009-10-30 16:15:19,086 DEBUG checkViewDepends()
2009-10-30 16:15:19,087 DEBUG running doUpdate() (showErrors=False)
2009-10-30 16:15:20,924 DEBUG openCache()
2009-10-30 16:15:23,756 DEBUG /openCache(), new cache size 26966
2009-10-30 16:15:23,756 DEBUG doPostInitialUpdate
2009-10-30 16:15:23,757 DEBUG Plugin modules in ./plugins: dpkg_status_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py langpack_manual_plugin.py deb_plugin.py
2009-10-30 16:15:23,757 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2009-10-30 16:15:23,759 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2009-10-30 16:15:23,759 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2009-10-30 16:15:23,760 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2009-10-30 16:15:23,760 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2009-10-30 16:15:23,761 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2009-10-30 16:15:23,762 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2009-10-30 16:15:23,763 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2009-10-30 16:15:23,763 DEBUG Loading module ./plugins/deb_plugin.py
2009-10-30 16:15:23,764 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2009-10-30 16:15:23,764 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2009-10-30 16:15:23,764 DEBUG plugins for condition 'karmicPostInitialUpdate' are '[]'
2009-10-30 16:15:23,764 DEBUG plugins for condition 'from_jauntyPostInitialUpdate' are '[]'
2009-10-30 16:15:23,764 DEBUG quirks: running karmicPostInitialUpdate
2009-10-30 16:15:23,765 DEBUG running karmicPostInitialUpdate
2009-10-30 16:15:25,159 DEBUG Foreign: wallpaper-balanzan-theme icon-balanzan-theme gtk-balanzan-theme gdm-balanzan-theme balanzan-theme gnome-balanzan-theme
2009-10-30 16:15:25,159 DEBUG Obsolete: adobe-flashplugin acetoneiso
2009-10-30 16:15:25,160 DEBUG updateSourcesList()
2009-10-30 16:15:25,271 DEBUG rewriteSourcesList()
2009-10-30 16:15:25,274 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted'
2009-10-30 16:15:25,274 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted' updated to new dist
2009-10-30 16:15:25,274 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted'
2009-10-30 16:15:25,275 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted' updated to new dist
2009-10-30 16:15:25,275 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted'
2009-10-30 16:15:25,275 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted' updated to new dist
2009-10-30 16:15:25,275 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted'
2009-10-30 16:15:25,275 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted' updated to new dist
2009-10-30 16:15:25,275 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe'
2009-10-30 16:15:25,276 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe' updated to new dist
2009-10-30 16:15:25,276 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe'
2009-10-30 16:15:25,276 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe' updated to new dist
2009-10-30 16:15:25,276 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe'
2009-10-30 16:15:25,276 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe' updated to new dist
2009-10-30 16:15:25,276 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe'
2009-10-30 16:15:25,276 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe' updated to new dist
2009-10-30 16:15:25,277 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse'
2009-10-30 16:15:25,277 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse' updated to new dist
2009-10-30 16:15:25,277 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse'
2009-10-30 16:15:25,277 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse' updated to new dist
2009-10-30 16:15:25,277 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse'
2009-10-30 16:15:25,277 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse' updated to new dist
2009-10-30 16:15:25,277 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse'
2009-10-30 16:15:25,278 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse' updated to new dist
2009-10-30 16:15:25,278 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted'
2009-10-30 16:15:25,278 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted' updated to new dist
2009-10-30 16:15:25,278 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted'
2009-10-30 16:15:25,278 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted' updated to new dist
2009-10-30 16:15:25,278 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe'
2009-10-30 16:15:25,278 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe' updated to new dist
2009-10-30 16:15:25,279 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe'
2009-10-30 16:15:25,279 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe' updated to new dist
2009-10-30 16:15:25,279 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse'
2009-10-30 16:15:25,279 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse' updated to new dist
2009-10-30 16:15:25,279 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse'
2009-10-30 16:15:25,279 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse' updated to new dist
2009-10-30 16:15:25,279 DEBUG examining: 'deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main'
2009-10-30 16:15:25,284 DEBUG entry '# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-10-30 16:15:25,284 DEBUG examining: 'deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main'
2009-10-30 16:15:25,288 DEBUG entry '# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-10-30 16:15:25,288 INFO fixing components inconsistency from 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted'
2009-10-30 16:15:25,288 INFO to new entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted'
2009-10-30 16:15:25,288 INFO fixing components inconsistency from 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted'
2009-10-30 16:15:25,288 INFO to new entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted'
2009-10-30 16:15:32,005 DEBUG running doUpdate() (showErrors=True)
2009-10-30 16:15:52,137 DEBUG openCache()
2009-10-30 16:15:52,593 DEBUG /openCache(), new cache size 1505
2009-10-30 16:15:52,594 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update
2009-10-30 16:16:20,762 DEBUG abort called
2009-10-30 16:16:20,763 DEBUG openCache()
2009-10-30 16:16:26,520 DEBUG /openCache(), new cache size 26966
2009-10-30 16:16:26,548 DEBUG enabling apt cron job

nothing in side term.log

---

### Post by otoris on 2009-10-30
I get the same message when I try to upgrade... Pretty annoying. Don't know what to do about it though.

---

### Post by Ofloo on 2009-10-31
I had the same issue.

[http://ubuntuforums.org/showthread.php?p=8206582#post8206582](http://ubuntuforums.org/showthread.php?p=8206582#post8206582)

---

