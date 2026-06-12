---
title: "Upgrade stuck, please help!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by rknoesel on 2009-04-25
I tried to upgrade my server installation from 8.10 to jaunty.  I was connected via ssh, and ran 'do-release-upgrade' after making sure everything was up to date.  Everything seemed to work fine until there was some text about services restarting (including ssh?), then my ssh session was disconnected.

That was a few hours ago, and the upgrade seems to be stuck.  It seems that there is now a dangling sshd process and the following processes seem to be update related:

> root     11618  0.1 16.1 246340 165704 pts/0   S+   02:12   0:13 /usr/bin/python /tmp/tmpnvaxt8/jaunty --mode=server --frontend=DistUpgradeViewText
root     11717  0.0 13.3 247236 136736 pts/0   S+   03:03   0:00 /usr/bin/python /tmp/tmpnvaxt8/jaunty --mode=server --frontend=DistUpgradeViewText
root     14279  0.0  0.3   9156  3664 pts/1    Ss+  03:03   0:00 /usr/bin/dpkg --force-overwrite --status-fd 55 --configure libc6
root     14280  0.0  1.0  52388 11204 pts/1    S+   03:03   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/libc6.postinst configure 2.8~20080505-0ubuntu9
root     14291  0.0  0.0   4024   672 pts/1    S+   03:03   0:00 /bin/sh /var/lib/dpkg/info/libc6.postinst configure 2.8~20080505-0ubuntu9
root     14341  0.0  0.2  19120  2188 pts/1    S+   03:03   0:00 whiptail --backtitle Package configuration --title Configuring libc6 --output-fd 11 --nocancel --inputbox -- Running services and
 programs that are using NSS need to be restarted, otherwise they might not be able to do lookup or authentication any more (for services such as ssh, this can affect your ability?to login). Ple
ase review the following space-separated list of init.d scripts for services to be restarted now, and correct it if needed.??Note: restarting sshd/telnetd should not affect any existing connecti
ons.??Services to restart for GNU libc library upgrade: 13 204 webmin vsftpd ssh samba rsync exim4 cron



Is there any way I can reconnect to that dangling ssh session?  I've tried restarting all the services mentioned in the whiptail process, but I'm not sure what '13' or '204' are...

How screwed am I?  Everything is still working ok on the server, but I'm pretty sure that the next time I reboot everything will be hoarked.

Thanks for any help!!

---

### Post by rknoesel on 2009-04-25
So... what I did was just kill the PID of the 'whiptail' process (which was just a dangling message box), after which the upgrade continued for a while.  At some point it simply stopped (who knows why), but since there were no more install processes running, I went ahead and rebooted.  Everything came up fine, and so I did an apt-get dist-upgrade, which went ahead and installed the rest of the crap.

Everything is upgraded to Jaunty now and works fine.

---

