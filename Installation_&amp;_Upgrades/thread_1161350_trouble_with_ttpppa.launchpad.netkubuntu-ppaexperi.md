---
title: "trouble with ttp://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by zika on 2009-05-16
very wisely I've enterd both ppa for KDE that are experimental in Software ources:
[http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu)
[http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu)
so I've got into a mess ... :)

I updated and upgraded today and got:

```
E: /var/cache/apt/archives/kdebase-runtime_4%3a4.2.85-0ubuntu1~jaunty1~ppa1_amd64.deb: trying to overwrite `/usr/lib/kconf_update_bin/phonon_deviceuids_update', which is also in package kdebase-runtime-data
E: /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a4.2.85-0ubuntu1~jaunty1~ppa1_amd64.deb: trying to overwrite `/usr/bin/keditfiletype', which is also in package kdebase-bin
E: /var/cache/apt/archives/libkonq5_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/share/kde4/apps/kconf_update/move_favicons.sh', which is also in package kdebase-data
E: /var/cache/apt/archives/kdebase-bin_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/bin/kbookmarkmerger', which is also in package konqueror
E: /var/cache/apt/archives/kdebase-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_all.deb: trying to overwrite `/usr/share/kde4/apps/keditbookmarks/keditbookmarksui.rc', which is also in package konqueror
E: /var/cache/apt/archives/kdebase-runtime-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa3_all.deb: trying to overwrite `/usr/share/kde4/apps/kstyle/themes/oxygen.themerc', which is also in package kde-icons-oxygen
E: /var/cache/apt/archives/libkonqsidebarplugin4_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/libkonqsidebarplugin.so.4', which is also in package konqueror
E: /var/cache/apt/archives/konqueror_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/konq_shellcmdplugin.so', which is also in package kdebase-bin
E: /var/cache/apt/archives/konqueror-nsplugins_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/libnsplugin.so', which is also in package kdebase-bin


E: /var/cache/apt/archives/kdebase-runtime_4%3a4.2.85-0ubuntu1~jaunty1~ppa1_amd64.deb: trying to overwrite `/usr/lib/kde4/kcm_filetypes.so', which is also in package kdebase-bin
E: /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a4.2.85-0ubuntu1~jaunty1~ppa1_amd64.deb: trying to overwrite `/usr/bin/keditfiletype', which is also in package kdebase-bin
E: /var/cache/apt/archives/libkonq5_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/kded_favicons.so', which is also in package kdebase-bin
E: /var/cache/apt/archives/kdebase-bin_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/bin/kbookmarkmerger', which is also in package konqueror
E: /var/cache/apt/archives/kdebase-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_all.deb: trying to overwrite `/usr/share/kde4/apps/keditbookmarks/keditbookmarksui.rc', which is also in package konqueror
E: /var/cache/apt/archives/libkonqsidebarplugin4_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/libkonqsidebarplugin.so.4', which is also in package konqueror
E: /var/cache/apt/archives/konqueror_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/konq_shellcmdplugin.so', which is also in package kdebase-bin
E: /var/cache/apt/archives/konqueror-nsplugins_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb: trying to overwrite `/usr/lib/kde4/libnsplugin.so', which is also in package kdebase-bin
```in Terminal with apt-get I've got:
```
ika@zika-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-bin: Depends: kdebase-data (= 4:4.2.3-0ubuntu1~jaunty1~ppa1) but it is not installed
  konqueror: Depends: kdebase-data (>= 4:4.2.3-0ubuntu1~jaunty1~ppa1) but it is not installed
E: Unmet dependencies. Try using -f.
zika@zika-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libkonqsidebarplugin4 dolphin kfind kdebase-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-bin kdebase-data libkonqsidebarplugin4
The following NEW packages will be installed:
  kdebase-data libkonqsidebarplugin4
The following packages will be upgraded:
  kdebase-bin
1 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/1473kB of archives.
After this operation, 1364kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 209592 files and directories currently installed.)
Preparing to replace kdebase-bin 4:4.2.3-0ubuntu1~jaunty1~ppa1 (using .../kdebase-bin_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb) ...
Unpacking replacement kdebase-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-bin_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/kbookmarkmerger', which is also in package konqueror
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-data (from .../kdebase-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_all.deb (--unpack):
 trying to overwrite `/usr/share/kde4/apps/keditbookmarks/keditbookmarksui.rc', which is also in package konqueror
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libkonqsidebarplugin4 (from .../libkonqsidebarplugin4_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkonqsidebarplugin4_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libkonqsidebarplugin.so.4', which is also in package konqueror
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-bin_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb
 /var/cache/apt/archives/kdebase-data_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_all.deb
 /var/cache/apt/archives/libkonqsidebarplugin4_4%3a4.2.85-0ubuntu1~jaunty1~ppa2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
zika@zika-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-bin: Depends: kdebase-data (= 4:4.2.3-0ubuntu1~jaunty1~ppa1) but it is not installed
  konqueror: Depends: kdebase-data (>= 4:4.2.3-0ubuntu1~jaunty1~ppa1) but it is not installed
E: Unmet dependencies. Try using -f.
```what now ... ?

I've tried sudo dpkg --configure -a but ...

---

### Post by zvacet on 2009-05-16
Try with 

```
sudo apt-get -f install
```

---

### Post by zika on 2009-05-16
> **zvacet said:**
> Try with 
```
sudo apt-get -f install
```
tried several times ... You can see the outcome in my original post.
packages that have broken dependencies are: kdebase-bin and konqueror.
what is funny is that everything works OK. just ...
I've managed to get in between these two ppa-s ... :)

p.s. after three runs through reload->mark->apply, I managed to clear the problem, I hope without collateral damage. it seems that it was a partial upgrade after all ... :)

---

### Post by gijsterbeek on 2009-05-18
Not solved yet, apparently. 

[http://kubuntuforums.net/forums/index.php?topic=3103850.0](http://kubuntuforums.net/forums/index.php?topic=3103850.0)

---

### Post by Amundsen on 2009-11-03
I was failing to start Ubuntu 9.10 after a upgrade ([/etc/fstab cannot yet be mounted -problem]("http://ubuntuforums.org/showthread.php?t=1301766")). Due to helpful comments on this forum, I managed to start it finally. The key was to realize use "dpkg --clear-avail" command before running other commands. Now I have exactly same problem than zika (I have installed KDE on Ubuntu earlier), but I can't make my wireless network to work anymore. It complains that NetworkManager not in use, so I can't access internet to fix it. Luckily I left Windows XP as a back-up system. First time I had to open it for two years...

I probably have to try to remove kubuntu-desktop package and run upgrade again...Any other ideas?

---

