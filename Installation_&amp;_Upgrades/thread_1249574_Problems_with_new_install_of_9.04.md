---
title: "Problems with new install of 9.04"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by LVWilliams on 2009-08-25
I have performed a clean install of Jaunty 9.04 but am having issues with update manager and synaptic package manager. I keep getting an error telling me there is no free space in the Ubuntu partition and I am unable to download and install packages because of this (there is over 15gb free). I am also getting an Error: Broken Count>0 which indicates broken or unmet dependencies. This has only happened since I attempted to update. Can someone please help me out? :confused:

---

### Post by LVWilliams on 2009-08-25
Apparently I have 51 broken packages and need to fix them before the downloads can be installed :mad: How do I go about the fixing?

---

### Post by mikewhatever on 2009-08-25
Can you post the output of the **df -h** command from Terminal to verify the amount of space.

> **LVWilliams said:**
> Apparently I have 51 broken packages and need to fix them before the downloads can be installed :mad: How do I go about the fixing?

Try this guide: [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by LVWilliams on 2009-08-28
Here is the output I get using the -d command:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  alsa-base: Depends: lsof (>= 4.64) but it is not installed
  brasero: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  ekiga: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  eog: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  evince: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  evolution: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  fast-user-switch-applet: Depends: libxau6 but it is not installed
  file-roller: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gcalctool: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gconf-editor: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gdm: Depends: libxau6 but it is not installed
  gedit: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-games: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-media: Depends: libgnome-media0 but it is not installed
               Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-nettool: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-session: Depends: libxau6 but it is not installed
  gnome-system-monitor: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-terminal: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gnome-utils: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  gucharmap: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  language-pack-gnome-pt: Depends: language-pack-gnome-pt-base (>= 1:9.04+20090413) but it is not installed
                          Recommends: gnome-user-guide-pt but it is not installed
  language-pack-gnome-xh: Depends: language-pack-gnome-xh-base (>= 1:9.04+20090413) but it is not installed
  language-pack-pt: Depends: language-pack-pt-base (>= 1:9.04+20090413) but it is not installed
  language-pack-xh: Depends: language-pack-xh-base (>= 1:9.04+20090413) but it is not installed
  libbrasero-media0: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  libgdict-1.0-6: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  libgtop2-7: Depends: libxau6 but it is not installed
  libgucharmap7: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  liblpint-bonobo0: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  libparse-debianchangelog-perl: Depends: libio-string-perl but it is not installed
  libxcb-render0: Depends: libxau6 but it is not installed
  libxcb1: Depends: libxau6 but it is not installed
  libxext6: Depends: libxau6 but it is not installed
  libxp6: Depends: libxau6 but it is not installed
  lockfile-progs: Depends: liblockfile1 (>= 1.0) but it is not installed
  nautilus: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  pidgin: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  python-gnome2-desktop: Depends: libgnome-media0 but it is not installed
  python-launchpad-integration: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  rhythmbox: Depends: libgnome-media0 but it is not installed
             Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  seahorse: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  synaptic: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  totem-gstreamer: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  ubiquity-frontend-gtk: Depends: libxau6 but it is not installed
  ubuntu-desktop: Depends: gnome-power-manager but it is not installed
  ubuntu-standard: Depends: lsof but it is not installed
  update-notifier: Depends: libxau6 but it is not installed
  vinagre: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
  x11-xserver-utils: Depends: libxau6 but it is not installed
  xauth: Depends: libxau6 but it is not installed
  xserver-xorg-core: Depends: libxau6 but it is not installed
  yelp: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
E: Unmet dependencies. Try using -f.


This is the error I get from terminal when I use sudo apt-get install -f:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 27062 package `cups':
 EOF during value of field `Depends' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)

What can I do next?

---

### Post by LVWilliams on 2009-08-28
Sorry, wrong command from the noob here :(

THIS is what I get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.3G     0 100% /
tmpfs                 178M     0  178M   0% /lib/init/rw
varrun                178M  112K  178M   1% /var/run
varlock               178M  4.0K  178M   1% /var/lock
udev                  178M  180K  178M   1% /dev
tmpfs                 178M  720K  177M   1% /dev/shm
lrm                   178M  2.4M  175M   2% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp

---

### Post by Partyboi2 on 2009-08-28
Hi, your /dev/sda7 partition is full, if you are able to you would be better of increasing the size of your /dev/sda7 as it is only a 2.3 gig partition, you can do this  by booting a Ubuntu live cd and using gparted (System>Admin>Partition Editor) to resize your partitions to increase the size of /dev/sda7.

---

### Post by LVWilliams on 2009-08-28
Cheers! I'll give it a go shortly.

---

