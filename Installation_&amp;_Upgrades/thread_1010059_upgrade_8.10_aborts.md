---
title: "upgrade 8.10 aborts"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by 3blaxcatz on 2008-12-13
[FONT="Arial"]Hello,
I have just tried for the 4th time today to upgrade from 8.04 - 8.10 

Set-up gets to the second checking stage and then says it will abort set-up and tells me that there is not enough space on '/' and that I should remove stuff from the deleted folder and temporary packages from previous installations

Found a great tutorial 
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07) 

I have followed most of the bits I could understand e.g. ‘sudo’ bits and I have downloaded the fslint but do not know what is and is not safe from me to remove from '/'

I got rid of duplicates first as per the tutorials as this bit was easy for me to understand 

I think everything taking up space has gone

But it still says I need to remove at least 2522k from '/'

Can anyone advise?
[/FONT]

---

### Post by taurus on 2008-12-13
You can clean out your cache with

```
sudo apt-get clean
```
Also, make sure you empty trash bin for your account and root as well since files in there will still take up space.  In addition, check your /var/backups to make sure you don't have backup copies of your system.

```
df -h
sudo du -h /var/backups
```

---

### Post by 3blaxcatz on 2008-12-13
thanks for the reply
i have done the first bit that you suggest
[COLOR="darkred"]sudo apt-get clean[/COLOR]

can you tell me _really simply _how i do the second bit

[COLOR="DarkRed"]Also, make sure you empty trash bin for your account and root as well since files in there will still take up space. 
In addition, check your /var/backups to make sure you don't have backup copies of your system.
Code:
df -h
sudo du -h /var/backups[/COLOR]

is trash bin the same as the deleted items folder?
if so I have check that and removed everything

---

### Post by taurus on 2008-12-13
Can you post the outputs of the last two commands (type one line at a time) from the previous post?

---

### Post by 3blaxcatz on 2008-12-13
[COLOR="DarkRed"]df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  2.6G  990M  73% /
varrun                221M  104K  220M   1% /var/run
varlock               221M     0  221M   0% /var/lock
udev                  221M   52K  220M   1% /dev
devshm                221M   12K  221M   1% /dev/shm
lrm                   221M   39M  182M  18% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      3.8G  2.6G  990M  73% /home/blaxcatz/.gvfs
/dev/sdb1             6.1G  2.8G  3.3G  46% /media/disk

sudo du -h /var/backups
3.2M	/var/backups[/COLOR]

hopefully this makes sense to you

---

### Post by taurus on 2008-12-13
Looks like you didn't give yourself a whole lot of space when you installed Ubuntu, almost 4GB.

What's the output of this command from a terminal?

```
sudo du -h /var
```

---

### Post by 3blaxcatz on 2008-12-13
[COLOR="DarkRed"][COLOR="DarkRed"]sudo du -h /var

4.0K	/var/opt
0	/var/run/sudo/blaxcatz
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
4.0K	/var/games
8.0K	/var/lib/urandom
8.0K	/var/lib/dbus
12K	/var/lib/dhcp3
92K	/var/lib/doc-base/info
8.0K	/var/lib/doc-base/omf/pnm2ppa-color
8.0K	/var/lib/doc-base/omf/doc-base
8.0K	/var/lib/doc-base/omf/diveintopython
8.0K	/var/lib/doc-base/omf/nat
8.0K	/var/lib/doc-base/omf/ispell-manual
8.0K	/var/lib/doc-base/omf/dc
8.0K	/var/lib/doc-base/omf/gimp-help-en
8.0K	/var/lib/doc-base/omf/cupsys
8.0K	/var/lib/doc-base/omf/fdutils
8.0K	/var/lib/doc-base/omf/man-db
8.0K	/var/lib/doc-base/omf/gnupginterface
8.0K	/var/lib/doc-base/omf/pnm2ppa-calibrate
8.0K	/var/lib/doc-base/omf/packet-filter
8.0K	/var/lib/doc-base/omf/install-docs-man
8.0K	/var/lib/doc-base/omf/fdutils-faq
8.0K	/var/lib/doc-base/omf/pnm2ppa-ppa_networking
8.0K	/var/lib/doc-base/omf/time
8.0K	/var/lib/doc-base/omf/nano-faq
148K	/var/lib/doc-base/omf
92K	/var/lib/doc-base/documents
336K	/var/lib/doc-base
4.0K	/var/lib/hal
4.0K	/var/lib/PolicyKit-public
4.0K	/var/lib/guidance-backends
12K	/var/lib/update-notifier/user.d
16K	/var/lib/update-notifier
4.0K	/var/lib/initscripts
32K	/var/lib/xml-core
4.0K	/var/lib/aptitude
16K	/var/lib/initramfs-tools
108K	/var/lib/scrollkeeper/nl
60K	/var/lib/scrollkeeper/mr
60K	/var/lib/scrollkeeper/as
60K	/var/lib/scrollkeeper/lb
60K	/var/lib/scrollkeeper/my
80K	/var/lib/scrollkeeper/pl
264K	/var/lib/scrollkeeper/fr
120K	/var/lib/scrollkeeper/pt
60K	/var/lib/scrollkeeper/ml
60K	/var/lib/scrollkeeper/nn
60K	/var/lib/scrollkeeper/gu
68K	/var/lib/scrollkeeper/he
148K	/var/lib/scrollkeeper/uk
196K	/var/lib/scrollkeeper/ru
64K	/var/lib/scrollkeeper/lv
72K	/var/lib/scrollkeeper/en
72K	/var/lib/scrollkeeper/sr
76K	/var/lib/scrollkeeper/vi
172K	/var/lib/scrollkeeper/pt_BR
268K	/var/lib/scrollkeeper/es
268K	/var/lib/scrollkeeper/C
196K	/var/lib/scrollkeeper/it
104K	/var/lib/scrollkeeper/zh_TW
60K	/var/lib/scrollkeeper/am
92K	/var/lib/scrollkeeper/cs
68K	/var/lib/scrollkeeper/be
64K	/var/lib/scrollkeeper/et
92K	/var/lib/scrollkeeper/sk
60K	/var/lib/scrollkeeper/uz
140K	/var/lib/scrollkeeper/el
60K	/var/lib/scrollkeeper/fo
60K	/var/lib/scrollkeeper/ur
116K	/var/lib/scrollkeeper/hu
160K	/var/lib/scrollkeeper/ko
60K	/var/lib/scrollkeeper/ia
60K	/var/lib/scrollkeeper/sr@Latn
128K	/var/lib/scrollkeeper/de
68K	/var/lib/scrollkeeper/nb
60K	/var/lib/scrollkeeper/hy
60K	/var/lib/scrollkeeper/te
60K	/var/lib/scrollkeeper/mg
60K	/var/lib/scrollkeeper/li
96K	/var/lib/scrollkeeper/ro
60K	/var/lib/scrollkeeper/sq
60K	/var/lib/scrollkeeper/ku
60K	/var/lib/scrollkeeper/lg
60K	/var/lib/scrollkeeper/sw
5.3M	/var/lib/scrollkeeper/index
60K	/var/lib/scrollkeeper/mi
68K	/var/lib/scrollkeeper/kn
156K	/var/lib/scrollkeeper/ca
60K	/var/lib/scrollkeeper/ka
60K	/var/lib/scrollkeeper/hr
60K	/var/lib/scrollkeeper/ky
60K	/var/lib/scrollkeeper/wa
60K	/var/lib/scrollkeeper/co
60K	/var/lib/scrollkeeper/ga
72K	/var/lib/scrollkeeper/gl
72K	/var/lib/scrollkeeper/is
72K	/var/lib/scrollkeeper/id
136K	/var/lib/scrollkeeper/fi
60K	/var/lib/scrollkeeper/cy
60K	/var/lib/scrollkeeper/rm
60K	/var/lib/scrollkeeper/eo
60K	/var/lib/scrollkeeper/yo
60K	/var/lib/scrollkeeper/or
60K	/var/lib/scrollkeeper/yi
60K	/var/lib/scrollkeeper/af
60K	/var/lib/scrollkeeper/xh
60K	/var/lib/scrollkeeper/az
5.9M	/var/lib/scrollkeeper/TOC
60K	/var/lib/scrollkeeper/br
60K	/var/lib/scrollkeeper/ug
64K	/var/lib/scrollkeeper/ms
60K	/var/lib/scrollkeeper/tl
60K	/var/lib/scrollkeeper/rw
60K	/var/lib/scrollkeeper/bn
60K	/var/lib/scrollkeeper/bs
60K	/var/lib/scrollkeeper/ne
60K	/var/lib/scrollkeeper/tg
148K	/var/lib/scrollkeeper/en_GB
60K	/var/lib/scrollkeeper/wo
60K	/var/lib/scrollkeeper/no
104K	/var/lib/scrollkeeper/eu
60K	/var/lib/scrollkeeper/se
120K	/var/lib/scrollkeeper/bg
60K	/var/lib/scrollkeeper/lo
60K	/var/lib/scrollkeeper/th
72K	/var/lib/scrollkeeper/da
60K	/var/lib/scrollkeeper/an
60K	/var/lib/scrollkeeper/sl
124K	/var/lib/scrollkeeper/pa
60K	/var/lib/scrollkeeper/kk
76K	/var/lib/scrollkeeper/ar
60K	/var/lib/scrollkeeper/mn
196K	/var/lib/scrollkeeper/oc
68K	/var/lib/scrollkeeper/tr
64K	/var/lib/scrollkeeper/lt
60K	/var/lib/scrollkeeper/zu
60K	/var/lib/scrollkeeper/fa
148K	/var/lib/scrollkeeper/zh_CN
252K	/var/lib/scrollkeeper/sv
60K	/var/lib/scrollkeeper/si
60K	/var/lib/scrollkeeper/ta
60K	/var/lib/scrollkeeper/tk
116K	/var/lib/scrollkeeper/ja
21M	/var/lib/scrollkeeper
4.0K	/var/lib/NetworkManager
12K	/var/lib/locales/supported.d
16K	/var/lib/locales
12K	/var/lib/dictionaries-common/wordlist
12K	/var/lib/dictionaries-common/ispell
8.0K	/var/lib/dictionaries-common/aspell
36K	/var/lib/dictionaries-common
8.0K	/var/lib/thunderbird/extensions.d
12K	/var/lib/thunderbird
4.0K	/var/lib/snmp
4.0K	/var/lib/synaptic
76K	/var/lib/gconf/debian.defaults
58M	/var/lib/gconf/defaults
58M	/var/lib/gconf
12K	/var/lib/PolicyKit
4.0K	/var/lib/dpkg/updates
4.0K	/var/lib/dpkg/parts
37M	/var/lib/dpkg/info
16K	/var/lib/dpkg/triggers
268K	/var/lib/dpkg/alternatives
42M	/var/lib/dpkg
4.0K	/var/lib/gnome-session
4.0K	/var/lib/deborphan
12K	/var/lib/ufw
16K	/var/lib/python-support/python2.5/dbus/mainloop
180K	/var/lib/python-support/python2.5/dbus
76K	/var/lib/python-support/python2.5/gdata/calendar
44K	/var/lib/python-support/python2.5/gdata/apps
48K	/var/lib/python-support/python2.5/gdata/base
28K	/var/lib/python-support/python2.5/gdata/docs
52K	/var/lib/python-support/python2.5/gdata/spreadsheet
416K	/var/lib/python-support/python2.5/gdata
376K	/var/lib/python-support/python2.5/orca/scripts
1.6M	/var/lib/python-support/python2.5/orca
68K	/var/lib/python-support/python2.5/atom
156K	/var/lib/python-support/python2.5/xdg
36K	/var/lib/python-support/python2.5/glchess/ui
200K	/var/lib/python-support/python2.5/glchess/scene/opengl
56K	/var/lib/python-support/python2.5/glchess/scene/cairo
284K	/var/lib/python-support/python2.5/glchess/scene
92K	/var/lib/python-support/python2.5/glchess/ggz
140K	/var/lib/python-support/python2.5/glchess/gtkui
88K	/var/lib/python-support/python2.5/glchess/chess/fics
196K	/var/lib/python-support/python2.5/glchess/chess
944K	/var/lib/python-support/python2.5/glchess
100K	/var/lib/python-support/python2.5/gnome_sudoku/gtk_goodies
448K	/var/lib/python-support/python2.5/gnome_sudoku
88K	/var/lib/python-support/python2.5/gtk-2.0/gtk
60K	/var/lib/python-support/python2.5/gtk-2.0/gobject
16K	/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop
20K	/var/lib/python-support/python2.5/gtk-2.0/evolution
44K	/var/lib/python-support/python2.5/gtk-2.0/gnome
16K	/var/lib/python-support/python2.5/gtk-2.0/pynotify
24K	/var/lib/python-support/python2.5/gtk-2.0/bonobo
20K	/var/lib/python-support/python2.5/gtk-2.0/gnomevfs
16K	/var/lib/python-support/python2.5/gtk-2.0/totem
20K	/var/lib/python-support/python2.5/gtk-2.0/gnomeprint
428K	/var/lib/python-support/python2.5/gtk-2.0
88K	/var/lib/python-support/python2.5/invest
5.1M	/var/lib/python-support/python2.5
5.1M	/var/lib/python-support
4.0K	/var/lib/sgml-base
8.0K	/var/lib/logrotate
4.0K	/var/lib/apparmor
176K	/var/lib/misc
52K	/var/lib/belocs
4.0K	/var/lib/update-manager
3.5M	/var/lib/aspell
8.0K	/var/lib/acpi-support
8.0K	/var/lib/avahi-autoipd
4.0K	/var/lib/libuuid
4.0K	/var/lib/vim/addons
8.0K	/var/lib/vim
3.3M	/var/lib/mlocate
12K	/var/lib/gdm/.fontconfig
28K	/var/lib/gdm
4.0K	/var/lib/apt/lists/partial
45M	/var/lib/apt/lists
12K	/var/lib/apt/keyrings
4.0K	/var/lib/apt/periodic
4.0K	/var/lib/apt/mirrors/partial
8.0K	/var/lib/apt/mirrors
45M	/var/lib/apt
12K	/var/lib/alsa
4.0K	/var/lib/displayconfig-gtk/locations
8.0K	/var/lib/displayconfig-gtk
24K	/var/lib/ucf/cache
72K	/var/lib/ucf
4.0K	/var/lib/xkb
24K	/var/lib/x11
124K	/var/lib/defoma/fontconfig.d
4.0K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
212K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
220K	/var/lib/defoma/x-ttcidfont-conf.d/dirs
600K	/var/lib/defoma/x-ttcidfont-conf.d
76K	/var/lib/defoma/scripts
4.0K	/var/lib/defoma/gs.d/dirs/CMap
124K	/var/lib/defoma/gs.d/dirs/fonts
132K	/var/lib/defoma/gs.d/dirs
236K	/var/lib/defoma/gs.d
144K	/var/lib/defoma/pango.d
144K	/var/lib/defoma/libwmf0.2-7.d
1.7M	/var/lib/defoma
178M	/var/lib
424K	/var/tmp/kdecache-blaxcatz
428K	/var/tmp
4.0K	/var/spool/cron/crontabs
8.0K	/var/spool/cron/atjobs
4.0K	/var/spool/cron/atspool
20K	/var/spool/cron
4.0K	/var/spool/cups-pdf/SPOOL
4.0K	/var/spool/cups-pdf/ANONYMOUS
12K	/var/spool/cups-pdf
4.0K	/var/spool/cups/tmp
16K	/var/spool/cups
4.0K	/var/spool/openoffice/uno_packages/cache
8.0K	/var/spool/openoffice/uno_packages
12K	/var/spool/openoffice
16K	/var/spool/anacron
80K	/var/spool
20K	/var/cache/man/fr.ISO8859-1
4.0K	/var/cache/man/opt
4.0K	/var/cache/man/cat1
24K	/var/cache/man/pl
32K	/var/cache/man/fr
4.0K	/var/cache/man/cat2
24K	/var/cache/man/ru
4.0K	/var/cache/man/cat4
20K	/var/cache/man/pt_BR
20K	/var/cache/man/es
24K	/var/cache/man/it
20K	/var/cache/man/zh_TW
20K	/var/cache/man/pl.UTF-8
20K	/var/cache/man/cs
4.0K	/var/cache/man/fsstnd
20K	/var/cache/man/hu
20K	/var/cache/man/ko
4.0K	/var/cache/man/cat6
20K	/var/cache/man/de
4.0K	/var/cache/man/cat3
20K	/var/cache/man/gl
20K	/var/cache/man/id
20K	/var/cache/man/fi
4.0K	/var/cache/man/cat8
4.0K	/var/cache/man/local
4.0K	/var/cache/man/X11R6
4.0K	/var/cache/man/oldlocal
4.0K	/var/cache/man/cat7
20K	/var/cache/man/it.UTF-8
20K	/var/cache/man/ru.UTF-8
20K	/var/cache/man/fr.UTF-8
4.0K	/var/cache/man/cat5
20K	/var/cache/man/ru.KOI8-R
20K	/var/cache/man/it.ISO8859-1
20K	/var/cache/man/pa
20K	/var/cache/man/tr
20K	/var/cache/man/zh_CN
20K	/var/cache/man/sv
20K	/var/cache/man/pl.ISO8859-2
24K	/var/cache/man/ja
956K	/var/cache/man
52K	/var/cache/ldconfig
924K	/var/cache/hald
5.0M	/var/cache/app-install
284K	/var/cache/fontconfig
4.0K	/var/cache/jockey
36K	/var/cache/dictionaries-common
4.0K	/var/cache/gnome-system-tools/backup
8.0K	/var/cache/gnome-system-tools
8.0K	/var/cache/system-tools-backends/backup/1/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/1/var/cache
16K	/var/cache/system-tools-backends/backup/1/var
20K	/var/cache/system-tools-backends/backup/1
8.0K	/var/cache/system-tools-backends/backup/2/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/2/var/cache
16K	/var/cache/system-tools-backends/backup/2/var
20K	/var/cache/system-tools-backends/backup/2
8.0K	/var/cache/system-tools-backends/backup/First/var/cache/system-tools-backends
12K	/var/cache/system-tools-backends/backup/First/var/cache
16K	/var/cache/system-tools-backends/backup/First/var
20K	/var/cache/system-tools-backends/backup/First
64K	/var/cache/system-tools-backends/backup
72K	/var/cache/system-tools-backends
4.0K	/var/cache/cups/ppd
4.0K	/var/cache/cups/rss
1.5M	/var/cache/cups
3.6M	/var/cache/debconf
4.0K	/var/cache/apt/archives/partial
24K	/var/cache/apt/archives
808K	/var/cache/apt
368K	/var/cache/hwtest
4.0K	/var/cache/pppconfig
4.0K	/var/cache/samba
14M	/var/cache
0	/var/lock
4.0K	/var/local
4.0K	/var/crash
4.0K	/var/log/unattended-upgrades
40K	/var/log/cups
12K	/var/log/fsck
616K	/var/log/installer
204K	/var/log/dist-upgrade
4.0K	/var/log/apparmor
4.0K	/var/log/news
24K	/var/log/gdm
76K	/var/log/apt
4.0K	/var/log/samba
3.5M	/var/log
3.2M	/var/backups
4.0K	/var/mail
199M	/var[/COLOR][/COLOR]

is this correct?

---

### Post by 3blaxcatz on 2008-12-15
o.k so what do i now?

---

### Post by taurus on 2008-12-15
Since you've giving yourself a small disk space for /, there is nothing much you can do except deleting a bunch of programs that you normally wouldn't use.

---

### Post by 3blaxcatz on 2008-12-16
o.k - thank you
being totally new to linux I would not have known how to do anything about the disk space size allocated when it installed - I assumed it had done what it needed to do.

Can you tell me what it should have been ideally?

which programs would you recommend I remove?

if I am lucky enough to get 8.10 installed how would I go about making the disk space bigger?

---

