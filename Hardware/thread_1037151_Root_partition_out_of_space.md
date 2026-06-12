---
title: "Root partition out of space"
date: 2009-01-11
forum: Hardware
---

### Post by dwdarkstar on 2009-01-11
[SIZE="3"]I installed Gutsy via the alternate disc on an Averatec 3200 series laptop with the following partitions: sda1 /root 3.7G, sda5 /home 31.2G, swap 880MB.  There is no free space left.  I then upgraded to Hardy via update manager.  My system has been running great until yesterday when I tried to install 25 updates via update manager.  Apparently my root partition is full, and now I get an error when I try to open update manager, depackge installer, and Synaptic package manager telling me:
[COLOR="Red"]E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/COLOR]
and suggesting that I run **dpkg --configure -a** in terminal.  The output is given below.  I'm not sure what to do as I've had bad experiences with partitions.  I have 25G free in my /home, can I transfer a few Gigs to my /root with out loosing everything?  Any help would be greatly appreciated.[/SIZE]

```
farstar@go-bot:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libdns35 (= 1:9.4.2.dfsg.P2-2ubuntu0.1); however:
  Version of libdns35 on system is 1:9.4.2.dfsg.P2-2.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libdns35 (= 1:9.4.2.dfsg.P2-2ubuntu0.1); however:
  Version of libdns35 on system is 1:9.4.2.dfsg.P2-2.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not installed.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-23-generic (2.6.24-23.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up libisccc30 (1:9.4.2.dfsg.P2-2ubuntu0.1) ...

dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.24-23-generic; however:
  Package linux-headers-2.6.24-23-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up ntpdate (1:4.2.4p4+dfsg-3ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up libisccfg30 (1:9.4.2.dfsg.P2-2ubuntu0.1) ...

Setting up liblwres30 (1:9.4.2.dfsg.P2-2ubuntu0.1) ...

Setting up linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.36) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libbind9-30 (1:9.4.2.dfsg.P2-2ubuntu0.1) ...

dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 dnsutils
 bind9-host
 linux-restricted-modules-generic
 linux-generic
 linux-headers-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic

```

---

### Post by taurus on 2009-01-11
What's the output of this command from a terminal?

```
df -h
```

---

### Post by dwdarkstar on 2009-01-11
[SIZE="3"]Hello taurus, the output is given below:[/SIZE]

```
farstar@go-bot:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.7G     0 100% /
varrun                220M  104K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   48K  220M   1% /dev
devshm                220M   12K  220M   1% /dev/shm
/dev/sda5              32G  6.2G   24G  21% /home
overflow              1.0M  388K  636K  38% /tmp

```

---

### Post by taurus on 2009-01-11
> **dwdarkstar said:**
> [SIZE="3"]Hello taurus, the output is given below:[/SIZE]

```
farstar@go-bot:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda1             3.7G  3.7G     0 100% /[/COLOR]**
varrun                220M  104K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   48K  220M   1% /dev
devshm                220M   12K  220M   1% /dev/shm
/dev/sda5              32G  6.2G   24G  21% /home
overflow              1.0M  388K  636K  38% /tmp

```

Well, you didn't give / partition a whole lot of space there.  Make sure you have empty the trash bin (as root) and clean out the cache.

```
sudo apt-get clean
```
Also, look in /var/backups to make sure you don't have a bunch of backup files taking up space.

```
sudo df -h /var
```

---

### Post by dwdarkstar on 2009-01-11
I cleaned the trash and posted the output below.  Forgive my ignorance, but is my system in trouble?

```
farstar@go-bot:~$ sudo apt-get clean
[sudo] password for farstar: 
farstar@go-bot:~$ sudo df -h /var
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.2G  370M  90% /

```

---

### Post by taurus on 2009-01-11
No, your system is not in trouble.  You just have to keep your eyes on the space on /.  Clean the cache to free up some space as frequent as you can.  Make sure there is nothing big taking up space in /var especially in /var/backups.  Sometimes, the system makes a backup (if you have it running in crontab) and stores it in /var/backups so just keep an eye on that.  Remember, don't remove anything that you are not sure because if you remove the wrong file/directory, you could crash your machine.

```
sudo du -h /var
```

---

### Post by dwdarkstar on 2009-01-11
Thanxs taurus,  there is a lot of stuff in /var.  /var/backups is holding 5.7M, but there is some bigger stuff further down.  So can I not "expand" /root somehow or transfer some memory from /home to give it space while maintaining my /home directory and my system overall?

```
farstar@go-bot:~$ sudo du -h /var
[sudo] password for farstar: 
72K	/var/log/apt
12K	/var/log/fsck
4.0K	/var/log/samba
296K	/var/log/installer/cdebconf
1.1M	/var/log/installer
4.0K	/var/log/news
4.0K	/var/log/apparmor
4.0K	/var/log/bittorrent
44K	/var/log/gdm
40K	/var/log/cups
640K	/var/log/dist-upgrade
4.0K	/var/log/unattended-upgrades
6.7M	/var/log
4.0K	/var/crash
4.0K	/var/opt
0	/var/run/grub
0	/var/run/sudo/farstar
0	/var/run/sudo
0	/var/run/console
8.0K	/var/run/hald
4.0K	/var/run/cups/certs
12K	/var/run/cups
8.0K	/var/run/avahi-daemon
8.0K	/var/run/NetworkManager
4.0K	/var/run/dbus
8.0K	/var/run/klogd
0	/var/run/PolicyKit
0	/var/run/screen
0	/var/run/pppconfig
4.0K	/var/run/network
0	/var/run/sendsigs.omit.d
104K	/var/run
4.0K	/var/mail
5.7M	/var/backups
16K	/var/spool/anacron
4.0K	/var/spool/cups/tmp
8.0K	/var/spool/cups
4.0K	/var/spool/cups-pdf/ANONYMOUS
8.0K	/var/spool/cups-pdf
4.0K	/var/spool/cron/crontabs
4.0K	/var/spool/cron/atspool
8.0K	/var/spool/cron/atjobs
20K	/var/spool/cron
4.0K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
24K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
16K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice/TypeDetection
20K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice
24K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org
28K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data
32K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry
44K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
4.0K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
4.0K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
88K	/var/spool/openoffice/uno_packages/cache/registry
8.0K	/var/spool/openoffice/uno_packages/cache/uno_packages/4zeGl9_/writer2latex.uno.pkg/META-INF
412K	/var/spool/openoffice/uno_packages/cache/uno_packages/4zeGl9_/writer2latex.uno.pkg
416K	/var/spool/openoffice/uno_packages/cache/uno_packages/4zeGl9_
420K	/var/spool/openoffice/uno_packages/cache/uno_packages
528K	/var/spool/openoffice/uno_packages/cache
532K	/var/spool/openoffice/uno_packages
536K	/var/spool/openoffice
592K	/var/spool
4.0K	/var/games
0	/var/lock
4.0K	/var/tmp
4.0K	/var/local
8.0K	/var/lib/logrotate
4.0K	/var/lib/apt/periodic
4.0K	/var/lib/apt/mirrors/partial
8.0K	/var/lib/apt/mirrors
12K	/var/lib/apt/keyrings
32K	/var/lib/apt/lists/partial
84M	/var/lib/apt/lists
84M	/var/lib/apt
4.0K	/var/lib/PolicyKit-public
4.0K	/var/lib/flashplugin-nonfree
3.5M	/var/lib/aspell
8.0K	/var/lib/tex-common/language-cnf
20K	/var/lib/tex-common/fontmap-cfg
12K	/var/lib/tex-common/fmtutil-cnf
44K	/var/lib/tex-common
4.0K	/var/lib/hal
62M	/var/lib/gconf/defaults
76K	/var/lib/gconf/debian.defaults
62M	/var/lib/gconf
28K	/var/lib/acpi-support
20K	/var/lib/x11
32K	/var/lib/xml-core
8.0K	/var/lib/avahi-autoipd
4.0K	/var/lib/initscripts
52K	/var/lib/belocs
4.0K	/var/lib/NetworkManager
3.8M	/var/lib/aptitude
16K	/var/lib/dpkg/triggers
40M	/var/lib/dpkg/info
4.0K	/var/lib/dpkg/updates
544K	/var/lib/dpkg/alternatives
4.0K	/var/lib/dpkg/parts
46M	/var/lib/dpkg
156K	/var/lib/doc-base/info
8.0K	/var/lib/doc-base/omf/install-docs-man
8.0K	/var/lib/doc-base/omf/nat
8.0K	/var/lib/doc-base/omf/pnm2ppa-ppa_networking
8.0K	/var/lib/doc-base/omf/packet-filter
8.0K	/var/lib/doc-base/omf/diveintopython
8.0K	/var/lib/doc-base/omf/nano-faq
8.0K	/var/lib/doc-base/omf/doc-base
8.0K	/var/lib/doc-base/omf/python-pysqlite2
8.0K	/var/lib/doc-base/omf/python-policy
8.0K	/var/lib/doc-base/omf/libpng12
8.0K	/var/lib/doc-base/omf/cupsys
8.0K	/var/lib/doc-base/omf/fdutils-faq
8.0K	/var/lib/doc-base/omf/dc
8.0K	/var/lib/doc-base/omf/fdutils
8.0K	/var/lib/doc-base/omf/java-policy
8.0K	/var/lib/doc-base/omf/libregexp-java
8.0K	/var/lib/doc-base/omf/fontconfig-user
8.0K	/var/lib/doc-base/omf/pnm2ppa-color
8.0K	/var/lib/doc-base/omf/libcommons-digester-java
8.0K	/var/lib/doc-base/omf/man-db
8.0K	/var/lib/doc-base/omf/debian-java-faq
8.0K	/var/lib/doc-base/omf/time
8.0K	/var/lib/doc-base/omf/gnupginterface
8.0K	/var/lib/doc-base/omf/ispell-manual
8.0K	/var/lib/doc-base/omf/gimp-help-en
8.0K	/var/lib/doc-base/omf/imagemagick
8.0K	/var/lib/doc-base/omf/pnm2ppa-calibrate
8.0K	/var/lib/doc-base/omf/libfreemarker-java
8.0K	/var/lib/doc-base/omf/libcommons-logging-java
236K	/var/lib/doc-base/omf
152K	/var/lib/doc-base/documents
548K	/var/lib/doc-base
4.0K	/var/lib/apparmor
4.0K	/var/lib/displayconfig-gtk/locations
8.0K	/var/lib/displayconfig-gtk
4.0K	/var/lib/bittorrent
4.0K	/var/lib/gnome-session
3.4M	/var/lib/mlocate
8.0K	/var/lib/dictionaries-common/aspell
12K	/var/lib/dictionaries-common/wordlist
12K	/var/lib/dictionaries-common/ispell
36K	/var/lib/dictionaries-common
8.0K	/var/lib/PolicyKit
4.0K	/var/lib/sgml-base
4.0K	/var/lib/vim/addons
8.0K	/var/lib/vim
52K	/var/lib/ucf/cache
128K	/var/lib/ucf
16K	/var/lib/gdm
4.0K	/var/lib/synaptic
4.0K	/var/lib/guidance-backends
12K	/var/lib/alsa
1.4M	/var/lib/gcj-4.2
4.0K	/var/lib/snmp
12K	/var/lib/locales/supported.d
16K	/var/lib/locales
8.0K	/var/lib/urandom
88K	/var/lib/python-support/python2.5/invest
52K	/var/lib/python-support/python2.5/gdata/spreadsheet
28K	/var/lib/python-support/python2.5/gdata/docs
76K	/var/lib/python-support/python2.5/gdata/calendar
44K	/var/lib/python-support/python2.5/gdata/apps
48K	/var/lib/python-support/python2.5/gdata/base
416K	/var/lib/python-support/python2.5/gdata
100K	/var/lib/python-support/python2.5/simplejson/tests
172K	/var/lib/python-support/python2.5/simplejson
36K	/var/lib/python-support/python2.5/gtk-2.0/gnome
88K	/var/lib/python-support/python2.5/gtk-2.0/gtk
60K	/var/lib/python-support/python2.5/gtk-2.0/gobject
24K	/var/lib/python-support/python2.5/gtk-2.0/bonobo
20K	/var/lib/python-support/python2.5/gtk-2.0/gnomevfs
16K	/var/lib/python-support/python2.5/gtk-2.0/pynotify
304K	/var/lib/python-support/python2.5/gtk-2.0
100K	/var/lib/python-support/python2.5/gnome_sudoku/gtk_goodies
448K	/var/lib/python-support/python2.5/gnome_sudoku
68K	/var/lib/python-support/python2.5/atom
376K	/var/lib/python-support/python2.5/orca/scripts
1.6M	/var/lib/python-support/python2.5/orca
92K	/var/lib/python-support/python2.5/glchess/ggz
140K	/var/lib/python-support/python2.5/glchess/gtkui
88K	/var/lib/python-support/python2.5/glchess/chess/fics
196K	/var/lib/python-support/python2.5/glchess/chess
36K	/var/lib/python-support/python2.5/glchess/ui
200K	/var/lib/python-support/python2.5/glchess/scene/opengl
56K	/var/lib/python-support/python2.5/glchess/scene/cairo
284K	/var/lib/python-support/python2.5/glchess/scene
944K	/var/lib/python-support/python2.5/glchess
16K	/var/lib/python-support/python2.5/dbus/mainloop
180K	/var/lib/python-support/python2.5/dbus
28K	/var/lib/python-support/python2.5/simplejson-1.7.3.egg-info
156K	/var/lib/python-support/python2.5/xdg
5.2M	/var/lib/python-support/python2.5
5.2M	/var/lib/python-support
8.0K	/var/lib/security
176K	/var/lib/misc
16K	/var/lib/seamonkey/chrome.d
284K	/var/lib/seamonkey/components
56K	/var/lib/seamonkey/chrome
360K	/var/lib/seamonkey
12K	/var/lib/dhcp3
4.0K	/var/lib/xkb
12K	/var/lib/ufw
4.0K	/var/lib/update-manager
8.0K	/var/lib/dbus
16K	/var/lib/initramfs-tools
4.0K	/var/lib/libuuid
12K	/var/lib/update-notifier/user.d
16K	/var/lib/update-notifier
164K	/var/lib/defoma/libwmf0.2-7.d
148K	/var/lib/defoma/pango.d
76K	/var/lib/defoma/scripts
4.0K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
284K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
292K	/var/lib/defoma/x-ttcidfont-conf.d/dirs
688K	/var/lib/defoma/x-ttcidfont-conf.d
136K	/var/lib/defoma/fontconfig.d
184K	/var/lib/defoma/gs.d/dirs/fonts
4.0K	/var/lib/defoma/gs.d/dirs/CMap
192K	/var/lib/defoma/gs.d/dirs
304K	/var/lib/defoma/gs.d
2.0M	/var/lib/defoma
256K	/var/lib/texmf/web2c/tex
164K	/var/lib/texmf/web2c/metafont
2.4M	/var/lib/texmf/web2c/pdftex
2.8M	/var/lib/texmf/web2c
92K	/var/lib/texmf/fonts/map/dvips/updmap
96K	/var/lib/texmf/fonts/map/dvips
24K	/var/lib/texmf/fonts/map/dvipdfm/updmap
28K	/var/lib/texmf/fonts/map/dvipdfm
52K	/var/lib/texmf/fonts/map/pdftex/updmap
56K	/var/lib/texmf/fonts/map/pdftex
184K	/var/lib/texmf/fonts/map
188K	/var/lib/texmf/fonts
12K	/var/lib/texmf/tex/generic/config
16K	/var/lib/texmf/tex/generic
20K	/var/lib/texmf/tex
3.2M	/var/lib/texmf
60K	/var/lib/scrollkeeper/an
60K	/var/lib/scrollkeeper/lt
60K	/var/lib/scrollkeeper/cs
60K	/var/lib/scrollkeeper/sw
68K	/var/lib/scrollkeeper/eu
60K	/var/lib/scrollkeeper/sq
60K	/var/lib/scrollkeeper/hy
212K	/var/lib/scrollkeeper/C
60K	/var/lib/scrollkeeper/bs
60K	/var/lib/scrollkeeper/rm
176K	/var/lib/scrollkeeper/oc
60K	/var/lib/scrollkeeper/mr
60K	/var/lib/scrollkeeper/zu
60K	/var/lib/scrollkeeper/gl
60K	/var/lib/scrollkeeper/az
60K	/var/lib/scrollkeeper/wo
72K	/var/lib/scrollkeeper/sr
60K	/var/lib/scrollkeeper/uz
60K	/var/lib/scrollkeeper/lg
76K	/var/lib/scrollkeeper/nl
60K	/var/lib/scrollkeeper/ms
196K	/var/lib/scrollkeeper/es
60K	/var/lib/scrollkeeper/lo
60K	/var/lib/scrollkeeper/en
68K	/var/lib/scrollkeeper/hu
144K	/var/lib/scrollkeeper/ru
60K	/var/lib/scrollkeeper/fa
60K	/var/lib/scrollkeeper/ar
60K	/var/lib/scrollkeeper/sk
60K	/var/lib/scrollkeeper/is
60K	/var/lib/scrollkeeper/as
64K	/var/lib/scrollkeeper/ro
60K	/var/lib/scrollkeeper/ka
60K	/var/lib/scrollkeeper/br
60K	/var/lib/scrollkeeper/tr
60K	/var/lib/scrollkeeper/rw
84K	/var/lib/scrollkeeper/ja
108K	/var/lib/scrollkeeper/ko
128K	/var/lib/scrollkeeper/it
60K	/var/lib/scrollkeeper/am
60K	/var/lib/scrollkeeper/pt
3.0M	/var/lib/scrollkeeper/index
60K	/var/lib/scrollkeeper/yi
68K	/var/lib/scrollkeeper/vi
60K	/var/lib/scrollkeeper/se
104K	/var/lib/scrollkeeper/bg
60K	/var/lib/scrollkeeper/hr
60K	/var/lib/scrollkeeper/id
60K	/var/lib/scrollkeeper/nn
68K	/var/lib/scrollkeeper/da
60K	/var/lib/scrollkeeper/nb
60K	/var/lib/scrollkeeper/li
60K	/var/lib/scrollkeeper/ug
60K	/var/lib/scrollkeeper/af
188K	/var/lib/scrollkeeper/sv
112K	/var/lib/scrollkeeper/pt_BR
60K	/var/lib/scrollkeeper/sl
84K	/var/lib/scrollkeeper/zh_CN
60K	/var/lib/scrollkeeper/or
76K	/var/lib/scrollkeeper/fi
60K	/var/lib/scrollkeeper/no
92K	/var/lib/scrollkeeper/pa
60K	/var/lib/scrollkeeper/tk
60K	/var/lib/scrollkeeper/te
60K	/var/lib/scrollkeeper/wa
84K	/var/lib/scrollkeeper/zh_TW
60K	/var/lib/scrollkeeper/bn
148K	/var/lib/scrollkeeper/uk
60K	/var/lib/scrollkeeper/tg
3.1M	/var/lib/scrollkeeper/TOC
60K	/var/lib/scrollkeeper/tl
116K	/var/lib/scrollkeeper/en_GB
60K	/var/lib/scrollkeeper/lb
60K	/var/lib/scrollkeeper/ky
60K	/var/lib/scrollkeeper/ku
60K	/var/lib/scrollkeeper/ur
100K	/var/lib/scrollkeeper/el
60K	/var/lib/scrollkeeper/he
136K	/var/lib/scrollkeeper/ca
60K	/var/lib/scrollkeeper/cy
192K	/var/lib/scrollkeeper/fr
60K	/var/lib/scrollkeeper/ml
60K	/var/lib/scrollkeeper/et
60K	/var/lib/scrollkeeper/lv
60K	/var/lib/scrollkeeper/sr@Latn
60K	/var/lib/scrollkeeper/ne
60K	/var/lib/scrollkeeper/ia
60K	/var/lib/scrollkeeper/kk
60K	/var/lib/scrollkeeper/co
60K	/var/lib/scrollkeeper/fo
60K	/var/lib/scrollkeeper/th
60K	/var/lib/scrollkeeper/si
60K	/var/lib/scrollkeeper/mg
60K	/var/lib/scrollkeeper/ga
60K	/var/lib/scrollkeeper/pl
60K	/var/lib/scrollkeeper/xh
60K	/var/lib/scrollkeeper/eo
60K	/var/lib/scrollkeeper/ta
60K	/var/lib/scrollkeeper/my
60K	/var/lib/scrollkeeper/mn
116K	/var/lib/scrollkeeper/de
60K	/var/lib/scrollkeeper/gu
68K	/var/lib/scrollkeeper/be
60K	/var/lib/scrollkeeper/yo
60K	/var/lib/scrollkeeper/kn
60K	/var/lib/scrollkeeper/mi
14M	/var/lib/scrollkeeper
229M	/var/lib
4.0K	/var/cache/gnome-system-tools/backup
8.0K	/var/cache/gnome-system-tools
4.0K	/var/cache/apt/archives/partial
96K	/var/cache/apt/archives
26M	/var/cache/apt
3.0M	/var/cache/flashplugin-nonfree
8.0K	/var/cache/jockey
20K	/var/cache/man/ru.KOI8-R
20K	/var/cache/man/cs
4.0K	/var/cache/man/cat4
20K	/var/cache/man/it.ISO8859-1
4.0K	/var/cache/man/fsstnd
4.0K	/var/cache/man/opt
20K	/var/cache/man/gl
4.0K	/var/cache/man/cat1
4.0K	/var/cache/man/cat3
20K	/var/cache/man/es
20K	/var/cache/man/hu
24K	/var/cache/man/ru
4.0K	/var/cache/man/cat5
20K	/var/cache/man/pl.UTF-8
4.0K	/var/cache/man/cat2
20K	/var/cache/man/tr
24K	/var/cache/man/ja
20K	/var/cache/man/ko
24K	/var/cache/man/it
20K	/var/cache/man/fr.UTF-8
4.0K	/var/cache/man/X11R6
4.0K	/var/cache/man/cat8
4.0K	/var/cache/man/oldlocal
20K	/var/cache/man/id
20K	/var/cache/man/pl.ISO8859-2
20K	/var/cache/man/sv
20K	/var/cache/man/pt_BR
20K	/var/cache/man/zh_CN
20K	/var/cache/man/fi
20K	/var/cache/man/pa
20K	/var/cache/man/zh_TW
32K	/var/cache/man/fr
20K	/var/cache/man/it.UTF-8
4.0K	/var/cache/man/local
4.0K	/var/cache/man/cat7
4.0K	/var/cache/man/cat6
24K	/var/cache/man/pl
20K	/var/cache/man/de
20K	/var/cache/man/fr.ISO8859-1
20K	/var/cache/man/ru.UTF-8
1000K	/var/cache/man
28K	/var/cache/system-tools-backends/backup/2/etc
32K	/var/cache/system-tools-backends/backup/2
8.0K	/var/cache/system-tools-backends/backup/1/etc
12K	/var/cache/system-tools-backends/backup/1
8.0K	/var/cache/system-tools-backends/backup/First/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/First/var/cache
16K	/var/cache/system-tools-backends/backup/First/var
20K	/var/cache/system-tools-backends/backup/First
68K	/var/cache/system-tools-backends/backup
76K	/var/cache/system-tools-backends
4.0K	/var/cache/samba
60K	/var/cache/ldconfig
36K	/var/cache/dictionaries-common
304K	/var/cache/fontconfig
4.0K	/var/cache/cups/ppd
4.0K	/var/cache/cups/rss
20K	/var/cache/cups
4.0K	/var/cache/fonts
5.1M	/var/cache/app-install
4.0M	/var/cache/debconf
4.0K	/var/cache/hwtest
4.0K	/var/cache/pppconfig
916K	/var/cache/hald
40M	/var/cache
282M	/var


```

---

### Post by aesis05401 on 2009-01-11
[Check this out]("http://ubuntuforums.org/showthread.php?t=898573")

There are a number of tips here for finding ALL trash on a system - some of this info was brand new to me. 

As for resizing, that is not my specialty as I deal almost entirely in VM environments that are only used for one type of task apiece.  I have had success using GParted (or a similar utility livecd) to place an image of a bootable system into a larger partition, set the boot flag, reboot and run an integrity check.

---

### Post by albinootje on 2009-01-11
> **dwdarkstar said:**
> I cleaned the trash and posted the output below.  Forgive my ignorance, but is my system in trouble?

```
farstar@go-bot:~$ sudo apt-get clean
[sudo] password for farstar: 
farstar@go-bot:~$ sudo df -h /var
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.2G  370M  90% /

```

Good. Please run the following now :
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean

```
Post any errors.

For the rest, I would suggest to make proper backups, and then use gparted to make your / partition a little bigger if possible (depends on how you partitioned before).

---

### Post by taurus on 2009-01-11
If you look in /var/log

```
ls -la /var/log
```
there should be a few .gz files which are the backup files of the system logs.  You can safely remove them.

---

### Post by dwdarkstar on 2009-01-11
[SIZE="3"]To [COLOR="DarkOrange"]taurus[/COLOR], I removed the .gz files from /var/log.  Also, one of the previous commands you had me run freed up ~500MB allowing me to run update manager and Synaptic, so thank you.[/SIZE]

[SIZE="3"]To [COLOR="DarkOrange"]albinootjem[/COLOR], dpkg --congifure -a ran clean, apt-get -f install ran clean and identified a number of packages that could be removed, which I did via apt-get autoremove.  apt-get clean ran clean; this procedure has freed up additional space, my system memory:[/SIZE]
```
farstar@go-bot:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.0G  497M  87% /
varrun                220M  104K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   48K  220M   1% /dev
devshm                220M   12K  220M   1% /dev/shm
lrm                   220M   39M  182M  18% /lib/modules/2.6.24-23-generic/volatile
/dev/sda5              32G  6.2G   24G  21% /home

```

[SIZE="3"]To [COLOR="DarkOrange"]aesis05401[/COLOR], thanxs for the link, quite useful![/SIZE]

[SIZE="3"]At this point I have some breathing room in / so thanks taurus for your help.  From here on is it your previous prescription of steady monitoring combined with apt-get cleans?  Also, for future reference, given a hypothetical system, say with a an 80G hard drive and 1G of RAM, how would you recommend a fresh install be partitioned?[/SIZE]

---

### Post by taurus on 2009-01-11
If I were to install Ubuntu on a 80GB with 1GB of RAM, I would create three partitions:  10GB for /, 2GB for swap, and whatever left for /home.

---

