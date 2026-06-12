---
title: "Synaptic Package Manager &quot;huge error&quot;"
date: 2008-10-05
forum: General Help
---

### Post by Vertoxic on 2008-10-05
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

anyone know what this?

---

### Post by drs305 on 2008-10-05
> **Vertoxic said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

anyone know what this?

Run this command to correct it, if you are asking what to do:
```
sudo dpkg --configure -a
```

---

### Post by cornelis spronk on 2008-10-05
I typed

sudo dpkg --configure -a

from the keyboard, and it did not work properly

Then I did a copy and paste from the previous item given by drs305, using the right mouse button and it seemed to delete the erroneous packages and a new download without error was possible.

Why was the copy and paste technique successful, and the keyboard type command unsuccessful?

---

### Post by Kinetic Being on 2008-10-05
did you spell everything correct, have correct spaces, and two "-"'s before "configure"?

---

### Post by tonybaqain on 2008-10-05
please paste the results of the following commands, regardless error or correct answer :
[list]
[*]dpkg --version
[*]uname -a
[*]dpkg -L dpkg
[*]mount
[/list]

---

### Post by cornelis spronk on 2008-10-05
I believe I did.  Is 1 space between sudo and dpkg correct?

---

### Post by cornelis spronk on 2008-10-05
I tried to copy and paste.  At the moment it does not seem to be working. 

Thanks for the very quick replies.  

I will examine the results in the terminal to see if I can learn anything from it.

---

### Post by tonybaqain on 2008-10-05
i was grabbing some informtion from your system, im still trying to help you out, if you prefer, just please paste back the information displayed by these commands so i can tell you what to do next.

have fun :)

---

### Post by cornelis spronk on 2008-10-05
OK.  Here it is.


 dpkg --version
Debian `dpkg' package management program version 1.14.16.6ubuntu1 (i386).
This is free software; see the GNU General Public Licence version 2 or
later for copying conditions. There is NO warranty.
See dpkg --licence for copyright and licence details.

 uname -a
Linux neil-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

 dpkg -L dpkg
/.
/etc
/etc/dpkg
/etc/dpkg/dpkg.cfg
/etc/dpkg/origins
/etc/dpkg/origins/debian
/etc/alternatives
/etc/alternatives/README
/etc/logrotate.d
/etc/logrotate.d/dpkg
/usr
/usr/share
/usr/share/dpkg
/usr/share/dpkg/archtable
/usr/share/dpkg/origins
/usr/share/dpkg/cputable
/usr/share/dpkg/ostable
/usr/share/dpkg/triplettable
/usr/share/locale
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/dpkg.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/dpkg.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/dpkg.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/dpkg.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/dpkg.mo
/usr/share/locale/dz
/usr/share/locale/dz/LC_MESSAGES
/usr/share/locale/dz/LC_MESSAGES/dpkg.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/dpkg.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/dpkg.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/dpkg.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/dpkg.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/dpkg.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/dpkg.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/dpkg.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/dpkg.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/dpkg.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/dpkg.mo
/usr/share/locale/km
/usr/share/locale/km/LC_MESSAGES
/usr/share/locale/km/LC_MESSAGES/dpkg.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/dpkg.mo
/usr/share/locale/ku
/usr/share/locale/ku/LC_MESSAGES
/usr/share/locale/ku/LC_MESSAGES/dpkg.mo
/usr/share/locale/mr
/usr/share/locale/mr/LC_MESSAGES
/usr/share/locale/mr/LC_MESSAGES/dpkg.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/dpkg.mo
/usr/share/locale/ne
/usr/share/locale/ne/LC_MESSAGES
/usr/share/locale/ne/LC_MESSAGES/dpkg.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/dpkg.mo
/usr/share/locale/nn
/usr/share/locale/nn/LC_MESSAGES
/usr/share/locale/nn/LC_MESSAGES/dpkg.mo
/usr/share/locale/pa
/usr/share/locale/pa/LC_MESSAGES
/usr/share/locale/pa/LC_MESSAGES/dpkg.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/dpkg.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/dpkg.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/dpkg.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/dpkg.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/dpkg.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/dpkg.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/dpkg.mo
/usr/share/locale/th
/usr/share/locale/th/LC_MESSAGES
/usr/share/locale/th/LC_MESSAGES/dpkg.mo
/usr/share/locale/tl
/usr/share/locale/tl/LC_MESSAGES
/usr/share/locale/tl/LC_MESSAGES/dpkg.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/dpkg.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/dpkg.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/dpkg.mo
/usr/share/man
/usr/share/man/de
/usr/share/man/de/man8
/usr/share/man/de/man8/dpkg-divert.8.gz
/usr/share/man/de/man8/install-info.8.gz
/usr/share/man/de/man8/start-stop-daemon.8.gz
/usr/share/man/de/man8/update-alternatives.8.gz
/usr/share/man/de/man8/cleanup-info.8.gz
/usr/share/man/de/man8/dpkg-statoverride.8.gz
/usr/share/man/de/man1
/usr/share/man/de/man1/dpkg-split.1.gz
/usr/share/man/de/man1/dpkg.1.gz
/usr/share/man/de/man1/dpkg-deb.1.gz
/usr/share/man/de/man1/dpkg-query.1.gz
/usr/share/man/de/man5
/usr/share/man/de/man5/dpkg.cfg.5.gz
/usr/share/man/fr
/usr/share/man/fr/man8
/usr/share/man/fr/man8/dpkg-divert.8.gz
/usr/share/man/fr/man8/install-info.8.gz
/usr/share/man/fr/man8/start-stop-daemon.8.gz
/usr/share/man/fr/man8/update-alternatives.8.gz
/usr/share/man/fr/man8/cleanup-info.8.gz
/usr/share/man/fr/man8/dpkg-statoverride.8.gz
/usr/share/man/fr/man1
/usr/share/man/fr/man1/dpkg-split.1.gz
/usr/share/man/fr/man1/dpkg.1.gz
/usr/share/man/fr/man1/dpkg-deb.1.gz
/usr/share/man/fr/man1/dpkg-query.1.gz
/usr/share/man/fr/man5
/usr/share/man/fr/man5/dpkg.cfg.5.gz
/usr/share/man/pl
/usr/share/man/pl/man8
/usr/share/man/pl/man8/dpkg-divert.8.gz
/usr/share/man/pl/man8/start-stop-daemon.8.gz
/usr/share/man/pl/man8/update-alternatives.8.gz
/usr/share/man/pl/man8/cleanup-info.8.gz
/usr/share/man/pl/man8/dpkg-statoverride.8.gz
/usr/share/man/pl/man1
/usr/share/man/pl/man1/dpkg-split.1.gz
/usr/share/man/pl/man1/dpkg.1.gz
/usr/share/man/pl/man1/dpkg-deb.1.gz
/usr/share/man/pl/man1/dpkg-query.1.gz
/usr/share/man/pl/man5
/usr/share/man/pl/man5/dpkg.cfg.5.gz
/usr/share/man/sv
/usr/share/man/sv/man8
/usr/share/man/sv/man8/dpkg-divert.8.gz
/usr/share/man/sv/man8/install-info.8.gz
/usr/share/man/sv/man8/start-stop-daemon.8.gz
/usr/share/man/sv/man8/update-alternatives.8.gz
/usr/share/man/sv/man8/cleanup-info.8.gz
/usr/share/man/sv/man8/dpkg-statoverride.8.gz
/usr/share/man/sv/man1
/usr/share/man/sv/man1/dpkg-split.1.gz
/usr/share/man/sv/man1/dpkg.1.gz
/usr/share/man/sv/man1/dpkg-deb.1.gz
/usr/share/man/sv/man1/dpkg-query.1.gz
/usr/share/man/sv/man5
/usr/share/man/sv/man5/dpkg.cfg.5.gz
/usr/share/man/man8
/usr/share/man/man8/dpkg-divert.8.gz
/usr/share/man/man8/install-info.8.gz
/usr/share/man/man8/start-stop-daemon.8.gz
/usr/share/man/man8/update-alternatives.8.gz
/usr/share/man/man8/cleanup-info.8.gz
/usr/share/man/man8/dpkg-statoverride.8.gz
/usr/share/man/man1
/usr/share/man/man1/dpkg-split.1.gz
/usr/share/man/man1/dpkg.1.gz
/usr/share/man/man1/dpkg-deb.1.gz
/usr/share/man/man1/dpkg-query.1.gz
/usr/share/man/hu
/usr/share/man/hu/man5
/usr/share/man/hu/man5/dpkg.cfg.5.gz
/usr/share/man/man5
/usr/share/man/man5/dpkg.cfg.5.gz
/usr/share/man/ja
/usr/share/man/ja/man1
/usr/share/man/ja/man1/dpkg.1.gz
/usr/share/man/ja/man8
/usr/share/man/ja/man8/update-alternatives.8.gz
/usr/share/perl5
/usr/share/perl5/Dpkg.pm
/usr/share/perl5/Dpkg
/usr/share/perl5/Dpkg/Gettext.pm
/usr/share/doc
/usr/share/doc/dpkg
/usr/share/doc/dpkg/changelog.gz
/usr/share/doc/dpkg/THANKS.gz
/usr/share/doc/dpkg/AUTHORS
/usr/share/doc/dpkg/README.api
/usr/share/doc/dpkg/README.feature-removal-schedule
/usr/share/doc/dpkg/copyright
/usr/share/doc/dpkg/changelog.Debian.gz
/usr/share/doc/dpkg/usertags.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/dpkg
/usr/bin
/usr/bin/dpkg
/usr/bin/dpkg-deb
/usr/bin/dpkg-query
/usr/bin/dpkg-split
/usr/bin/dpkg-trigger
/usr/lib
/usr/lib/dpkg
/usr/lib/dpkg/mksplit
/usr/sbin
/usr/sbin/install-info
/usr/sbin/cleanup-info
/usr/sbin/dpkg-divert
/usr/sbin/dpkg-statoverride
/usr/sbin/update-alternatives
/var
/var/lib
/var/lib/dpkg
/var/lib/dpkg/alternatives
/var/lib/dpkg/info
/var/lib/dpkg/parts
/var/lib/dpkg/updates
/sbin
/sbin/start-stop-daemon

 mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/neil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neil)

---

