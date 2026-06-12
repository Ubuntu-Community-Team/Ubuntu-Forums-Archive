---
title: "ircu problem ..."
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by hackedro on 2009-06-12
Hi, i have installed ircu with apt-get so in 10 seconds i had my irc server up and running .. my question is : where ircu files are stored ? I have found that with that autoinstaller a user *irc* was created with home folder in var/run/ircd. In /etc/ircd i have only ircd.conf / motd. I cant find the rest of the files installed by ircu. Can anybody tell me where i can find them ?

---

### Post by Partyboi2 on 2009-06-12
Hi have a look at
```
/usr/sbin/ircd-ircu
/usr/share/doc/ircd-ircu
/usr/share/doc/ircd-ircu/ChangeLog.gz
/usr/share/doc/ircd-ircu/events.txt.gz
/usr/share/doc/ircd-ircu/api.txt
/usr/share/doc/ircd-ircu/gline.txt.gz
/usr/share/doc/ircd-ircu/ircd_snprintf.txt.gz
/usr/share/doc/ircd-ircu/jupe.txt.gz
/usr/share/doc/ircd-ircu/log.txt.gz
/usr/share/doc/ircd-ircu/joinbuf.txt
/usr/share/doc/ircd-ircu/modebuf.txt.gz
/usr/share/doc/ircd-ircu/msgq.txt.gz
/usr/share/doc/ircd-ircu/motd.txt
/usr/share/doc/ircd-ircu/privileges.txt
/usr/share/doc/ircd-ircu/2.7-New.gz
/usr/share/doc/ircd-ircu/ChangeLog.10.gz
/usr/share/doc/ircd-ircu/ChangeLog.07
/usr/share/doc/ircd-ircu/Manual.gz
/usr/share/doc/ircd-ircu/history.pre24
/usr/share/doc/ircd-ircu/README.patches.gz
/usr/share/doc/ircd-ircu/README-2.6
/usr/share/doc/ircd-ircu/Authors.gz
/usr/share/doc/ircd-ircu/fda.txt.gz
/usr/share/doc/ircd-ircu/readme.chroot.gz
/usr/share/doc/ircd-ircu/iso-time.html
/usr/share/doc/ircd-ircu/p10.html
/usr/share/doc/ircd-ircu/readme.asll
/usr/share/doc/ircd-ircu/readme.crules.gz
/usr/share/doc/ircd-ircu/readme.iauth.gz
/usr/share/doc/ircd-ircu/readme.cvs
/usr/share/doc/ircd-ircu/readme.log.gz
/usr/share/doc/ircd-ircu/readme.gline
/usr/share/doc/ircd-ircu/changelog.gz
/usr/share/doc/ircd-ircu/readme.indent
/usr/share/doc/ircd-ircu/readme.jupe
/usr/share/doc/ircd-ircu/changelog.Debian.gz
/usr/share/doc/ircd-ircu/readme.www
/usr/share/doc/ircd-ircu/snomask.html
/usr/share/doc/ircd-ircu/strings.txt
/usr/share/doc/ircd-ircu/INSTALL
/usr/share/doc/ircd-ircu/README.Debian
/usr/share/doc/ircd-ircu/copyright
/usr/share/doc/ircd-ircu/README.gz
/usr/share/doc/ircd-ircu/RELEASE.NOTES.gz
/usr/share/doc/ircd-ircu/features.txt.gz
/usr/share/doc/ircd-ircu/send.txt.gz
/usr/share/doc/ircd-ircu/2.4.notes.gz
/usr/share/doc/ircd-ircu/overview.u2.9.gz
/usr/share/doc/ircd-ircu/example.conf.gz
/usr/share/doc/ircd-ircu/readme.features.gz
/usr/share/doc/ircd-ircu/readme.who.gz
/usr/share/man/man8/ircd-ircu.8.gz
/usr/share/lintian/overrides/ircd-ircu
/etc/ircd
/etc/ircd/ircd.conf
/etc/ircd/ircd.motd
/etc/init.d/ircd-ircu
/var/log/ircd
/var/run/ircd
```

---

### Post by Laryllan on 2009-11-29
[https://help.ubuntu.com/9.10/serverguide/C/serverguide.pdf](https://help.ubuntu.com/9.10/serverguide/C/serverguide.pdf)
Maybe this helps too...

---

