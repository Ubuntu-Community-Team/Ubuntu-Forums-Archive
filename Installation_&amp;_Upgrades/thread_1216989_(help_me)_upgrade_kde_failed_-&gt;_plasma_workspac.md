---
title: "(help me) upgrade kde failed -&gt; plasma workspace won't start"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Ajat on 2009-07-18
Hi people.. i need your help.
i upgraded to the latest kde of my kubuntu 9.04 jaunty, by adding  [http://ppa.launchpad.net](http://ppa.launchpad.net) to repistory. 

after ```
sudo apt-get upgrade
```about 81MB archieves are downloaded.. after i restart my computer, i got the error  message which tell that plasma workspace is failed to start, now when i got

```
ajat@Storophanthus> sudo apt-get upgrade
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-workspace-dev: Depends: kdebase-workspace-libs4+5 (= 4:4.2.2-0ubuntu2) but 4:4.2.96-0ubuntu2~jaunty1~ppa2 is installed
                         Depends: libkwineffects1 (= 4:4.2.2-0ubuntu2) but 4:4.2.96-0ubuntu2~jaunty1~ppa2 is installed
                         Depends: libkdecorations4 (= 4:4.2.2-0ubuntu2) but 4:4.2.96-0ubuntu2~jaunty1~ppa2 is installed
E: Unmet dependencies. Try using -f.

```and then sudo apt-get -f install gives
```
ajat@Storophanthus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  sip4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-dev
The following packages will be upgraded:
  kdebase-workspace-dev
1 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
Need to get 0B/160kB of archives.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 316028 files and directories currently installed.)
Preparing to replace kdebase-workspace-dev 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-dev_4%3a4.2.96-0ubuntu2~jaunty1~ppa2_i386.deb) ...
Unpacking replacement kdebase-workspace-dev ...
Replacing files in old package kdebase-workspace-data ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-dev_4%3a4.2.96-0ubuntu2~jaunty1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libkephal.so', which is also in package kdebase-workspace-bin
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-dev_4%3a4.2.96-0ubuntu2~jaunty1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
]
```

now my desktop is really amusing.. the window has no titlebar. task manager wont active. no wallpaper. no clock widget.. T_T

help please..
thanks.

---

### Post by Partyboi2 on 2009-07-18
Hi, open a terminal and overwrite the file
```
cd /var/cache/apt/archives
sudo dpkg --force-overwrite --install kdebase-workspace-dev_4%3a4.2.96-0ubuntu2~jaunty1~ppa2_i386.deb
```
then
```
sudo apt-get -f install
```

---

### Post by Ajat on 2009-07-19
> **Partyboi2 said:**
> Hi, open a terminal and overwrite the file
```
cd /var/cache/apt/archives
sudo dpkg --force-overwrite --install kdebase-workspace-dev_4%3a4.2.96-0ubuntu2~jaunty1~ppa2_i386.deb
```then
```
sudo apt-get -f install
```

wowww. that's work!

thanks alot!

---

