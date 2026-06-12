---
title: "snort and gnome-do-plugins errors"
date: 2008-08-01
forum: General Help
---

### Post by reilus on 2008-08-01
This is so frustrating.  I can't figure this out.  Snort simply does not work.  I've tried all the stupid tutorials on google, nothing works.  I want snort to work, or I want it gone.  

I'm reading to jump off a cliff over here--or at least go back to windoze.  This is unbelievable.  

6 hours of this crap:

user@user-user:~$ sudo apt-get -f installReading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

1 not fully installed or removed.

After this operation, 0B of additional disk space will be used.

Setting up snort (2.7.0-14) ...

 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found

 * Starting Network Intrusion Detection System  snort                            * /etc/snort/db-pending-config file found

 * Snort will not start as its database is not yet configured.

 * Please configure the database as described in

 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian

 * and remove /etc/snort/db-pending-config

invoke-rc.d: initscript snort, action "start" failed.

dpkg: error processing snort (--configure):

 subprocess post-installation script returned error exit status 6

Errors were encountered while processing:

 snort

E: Sub-process /usr/bin/dpkg returned an error code (1)



Then I keep getting crash reports.

Also, I can't install the gnome-do-plugins.  I tried synaptic, terminal, all this crap.  I get this nonsense:

The following packages will be upgraded:
  gnome-do-plugins
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1230kB of archives.
After this operation, 1901kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gnome-do-plugins
Install these packages without verification [y/N]? y
(Reading database ... 209597 files and directories currently installed.)
Preparing to replace gnome-do-plugins 0.4.0-0ubuntu2 (using .../gnome-do-plugins_0.5.98.0-0~hardy~ppa2_all.deb) ...
Unpacking replacement gnome-do-plugins ...
dpkg: error processing /var/cache/apt/archives/gnome-do-plugins_0.5.98.0-0~hardy~ppa2_all.deb (--unpack):
 trying to overwrite `/usr/share/gnome-do/plugins/Rhythmbox.dll', which is also in package gnome-do-plugin-rhythmbox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-do-plugins_0.5.98.0-0~hardy~ppa2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help me?  I'm about ready to take Ubuntu off.  I got crashes in windoze, I don't need another buggy and unstable operating system.

Please help me.

---

### Post by lvlo on 2008-08-02
Try to remove Gnome-Do and plugins then install it again.

Note: Rhythmbox plugin is already in "gnome-do-plugins" package, so you don't need to install "gnome-do-plugin-rhythmbox" again.

---

### Post by aeturner on 2008-09-17
I am having the same problem.  Were you able to complete your installation of Snort and, if so, what did you do?
Thanks!

---

