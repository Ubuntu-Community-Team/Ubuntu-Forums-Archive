---
title: "Machine or hardware check program"
date: 2015-10-23
forum: Hardware
---

### Post by deepakdeshp on 2015-10-23
Hello,
Is there any Hardware check program for AMD processors?
Where are the hardware errors logged?

---

### Post by TheFu on 2015-10-23
/var/log/ - for pre-systemd OSes.
Use **journalctl** for post-systemd OSes.

---

### Post by deepakdeshp on 2015-12-15
> **TheFu said:**
> /var/log/ - for pre-systemd OSes.
Use **journalctl** for post-systemd OSes.

Which files should I see to locate hardware errors?

```
ls /var/log
alternatives.log       dmesg.1.gz             pm-suspend.log.2.gz
alternatives.log.1     dmesg.2.gz             pm-suspend.log.3.gz
alternatives.log.2.gz  dmesg.3.gz             pycentral.log
alternatives.log.3.gz  dmesg.4.gz             samba
apache2                dpkg.log               speech-dispatcher
apt                    dpkg.log.1             syslog
aptitude               dpkg.log.2.gz          syslog.1
aptitude.1.gz          dpkg.log.3.gz          syslog.2
auth.log               faillog                syslog.2.gz
auth.log.1             fontconfig.log         syslog.4.gz
auth.log.2.gz          fsck                   syslog.5.gz
auth.log.3.gz          gpu-manager.log        syslog.6.gz
auth.log.4.gz          hp                     syslog.7.gz
boot                   installer              udev
boot.0                 kern.log               unattended-upgrades
boot.1.gz              kern.log.1             upstart
boot.2.gz              kern.log.2.gz          vbox-install.log
boot.3.gz              kern.log.3.gz          vmware
boot.4.gz              kern.log.4.gz          vmware-installer
boot.log               lastlog                vnetlib
boot-sav               mdm                    wtmp
bootstrap.log          mintsystem.log         wtmp.1
btmp                   pm-powersave.log       Xorg.0.log
btmp.1                 pm-powersave.log.1     Xorg.0.log.old
ConsoleKit             pm-powersave.log.2.gz  Xorg.20.log
cups                   pm-powersave.log.3.gz  Xorg.21.log
dmesg                  pm-suspend.log      

```

---

### Post by TheFu on 2015-12-15
I'd use **grep**.  If you need to look at the .gz files, use **gunzip -c** and pipe that into grep.  There might be a **zgrep** that will read compressed archives. I dunno, just see the command, but not sure what it does.

If you have a GUI, there is probably some GUI tool that will search log files. Never used one of those myself.

---

