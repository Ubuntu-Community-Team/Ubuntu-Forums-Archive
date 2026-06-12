---
title: "upgrading from 8.04 to 8.10"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by KiwiTayl on 2009-10-09
I'm trying to upgrade from 8.04 to 8.10 and I get the following:
[IMG]http://photos-f.ak.fbcdn.net/hphotos-ak-snc1/hs210.snc1/7722_147801269156_620539156_2761213_6106631_n.jpg[/IMG]
Ok, how do I find and get rid of the unofficial software packages not provided by Ubuntu so I can proceed?

Thanks.

---

### Post by mac9416 on 2009-10-09
Maybe we can find some details in /var/log/dist-upgrade/main-log.
Could you paste the contents here?

---

### Post by KiwiTayl on 2009-10-09
[COLOR="DarkGreen"]I think this is everything that came up in terminal after typing the following command-[/COLOR] [COLOR="Navy"]tom@tom-laptop:/var/log/dist-upgrade$ view main.log\:[/COLOR]

2009-10-09 08:32:58,768 INFO release-upgrader version '0.93.34' started
2009-10-09 08:32:59,045 DEBUG svg pixbuf loader failed (Error displaying image)
2009-10-09 08:32:59,162 DEBUG Using 'DistUpgradeViewGtk' view
2009-10-09 08:32:59,235 DEBUG enable dpkg --force-overwrite
2009-10-09 08:32:59,344 DEBUG lsb-release: 'hardy'
2009-10-09 08:32:59,344 DEBUG _pythonSymlinkCheck run
2009-10-09 08:32:59,344 DEBUG openCache()
2009-10-09 08:33:01,316 DEBUG /openCache()
2009-10-09 08:33:01,322 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2009-10-09 08:33:01,322 DEBUG checkViewDepends()
2009-10-09 08:33:01,322 DEBUG running doUpdate() (showErrors=False)
2009-10-09 08:33:03,691 DEBUG openCache()
2009-10-09 08:33:05,655 DEBUG /openCache()
2009-10-09 08:33:05,656 DEBUG doPostInitialUpdate
2009-10-09 08:33:05,656 DEBUG quirks: running intrepidPostInitialUpdate
2009-10-09 08:33:05,656 DEBUG running intrepidPostInitialUpdate
2009-10-09 08:33:09,398 DEBUG Foreign:
2009-10-09 08:33:09,399 DEBUG Obsolete: libdivxencore0-binary linux-headers-2.6.24-17 linux-ubuntu-modules-2.6.22-14-generic adobereader-plugin libdivx0-binary linux-restricted-modules-2.6.24-17-generic skype linux-image-2.6.17-10-generic linux-image-2.6.22-14-generic dvdshrink linux-restricted-modules-2.6.17-10-generic realplay adobereader-enu linux-image-2.6.17-11-generic linux-headers-2.6.24-17-generic libdivxdecore0-binary libdvdcss2 linux-ubuntu-modules-2.6.24-17-generic nvidia-kernel-2.6.22-14-generic linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-2.6.22-14-generic linux-restricted-modules-2.6.20-16-generic w32codecs linux-image-2.6.24-17-generic automatix2 linux-image-2.6.20-16-generic
2009-10-09 08:33:09,400 DEBUG updateSourcesList()
2009-10-09 08:33:09,468 DEBUG rewriteSourcesList()
2009-10-09 08:33:09,474 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner'
2009-10-09 08:33:09,475 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner' updated to new dist
2009-10-09 08:33:09,475 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse'
2009-10-09 08:33:09,475 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse' updated to new dist
2009-10-09 08:33:09,475 DEBUG examining: 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties'
@                                                                               
2009-10-09 08:33:09,400 DEBUG updateSourcesList()
2009-10-09 08:33:09,468 DEBUG rewriteSourcesList()
2009-10-09 08:33:09,474 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner'
2009-10-09 08:33:09,475 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner' updated to new dist
2009-10-09 08:33:09,475 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse'
2009-10-09 08:33:09,475 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse' updated to new dist
2009-10-09 08:33:09,475 DEBUG examining: 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties'
2009-10-09 08:33:09,475 DEBUG entry 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties' updated to new dist
2009-10-09 08:33:09,475 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted'
2009-10-09 08:33:09,476 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,476 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted'
2009-10-09 08:33:09,476 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,476 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted'
2009-10-09 08:33:09,476 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,476 DEBUG examining: 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted'
2009-10-09 08:33:09,477 DEBUG entry 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,477 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted'
2009-10-09 08:33:09,477 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,477 DEBUG examining: 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted'
2009-10-09 08:33:09,477 DEBUG entry 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,477 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted'
2009-10-09 08:33:09,478 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,478 DEBUG examining: 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports universe main multiverse restricted'
2009-10-09 08:33:09,478 DEBUG entry 'deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted' updated to new dist
2009-10-09 08:33:09,478 DEBUG examining: 'deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free'
2009-10-09 08:33:09,481 DEBUG entry '# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free' was disabled (unknown mirror)
2009-10-09 08:33:15,261 DEBUG running doUpdate() (showErrors=True)
2009-10-09 08:35:05,299 DEBUG openCache()
2009-10-09 08:35:12,687 DEBUG /openCache()
2009-10-09 08:35:18,026 DEBUG Installing 'ash' (priority in required set 'required' but not scheduled for install)
2009-10-09 08:35:18,745 DEBUG Running KeepInstalledSection rules
2009-10-09 08:35:18,843 DEBUG Kernel uname: '2.6.24-24-generic'
2009-10-09 08:35:18,857 DEBUG nvidiaUpdate()
2009-10-09 08:35:18,898 DEBUG Removing 'nvidia-glx-new' (old nvidia driver)
2009-10-09 08:35:19,104 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2009-10-09 08:35:19,105 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2009-10-09 08:35:19,316 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2009-10-09 08:35:19,537 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2009-10-09 08:35:19,537 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2009-10-09 08:35:19,537 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2009-10-09 08:35:19,742 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2009-10-09 08:35:19,949 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2009-10-09 08:35:19,950 DEBUG quirks: running intrepidPostDistUpgradeCache
2009-10-09 08:35:19,950 DEBUG running intrepidPostDistUpgradeCache
2009-10-09 08:35:20,041 DEBUG Removing 'landscape-client' (custom landscape stub removal rule)
2009-10-09 08:35:20,462 DEBUG Installing 'landscape-common' (custom landscape-common stub install rule (to ensure its nor marked for auto-remove))
2009-10-09 08:44:40,676 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2009-10-09 08:44:40,678 DEBUG openCache()
2009-10-09 08:44:41,355 DEBUG /openCache()

---

### Post by mac9416 on 2009-10-09
Someone seems to have found a solution here: [http://ubuntuforums.org/showthread.php?t=770113&page=3](http://ubuntuforums.org/showthread.php?t=770113&page=3)

> log file contained just "Unable to correct problems, you have held broken packages" without details and Synaptic did not show any problem packages either, but before error message log mentioned "language-support-ru"
When I removed that package by Synaptic - whole update went smoothly 

For you, that packages could be landscape-common or landscape-client. Can you remove those and reinstall them after the upgrade?

Also, folks have mentioned disabling third-party repos. You might want to do that.

---

### Post by KiwiTayl on 2009-10-09
[COLOR="DarkGreen"]I did get a suggestion to disable 3rd party repos & did that, but the problem (which seems the same as mentioned) is finding the offending packages. I'll try your suggestion.

Thanks![/COLOR]

---

