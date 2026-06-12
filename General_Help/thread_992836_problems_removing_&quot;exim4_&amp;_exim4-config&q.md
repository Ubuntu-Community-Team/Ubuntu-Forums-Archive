---
title: "problems removing &quot;exim4 &amp; exim4-config&quot;"
date: 2008-11-25
forum: General Help
---

### Post by PeacefulWarrior on 2008-11-25
Hi there,

I cannot successfully remove an application that seems to be corrupted.
Kindly assist :-)

have tried :
[COLOR="Red"]apt-get remove exim4
apt-get autoremove exim4
apt-get autoremove exim4-config
[/COLOR]
root@anton-desktop:~# [COLOR="Red"]apt-get autoremove exim4[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package exim4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 197 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up exim4-config (4.69-2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
**  Package exim4-config is not configured yet.**
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
[B]dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigure[/B]d
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
**E: Sub-process /usr/bin/dpkg returned an error code (1)**

[COLOR="Red"]even "apt-get install exim4  exim4-config" doesn't work???[/COLOR]

root@anton-desktop:~# apt-get install exim4  exim4-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exim4-config is already the newest version.
exim4-config set to manually installed.
The following NEW packages will be installed:
  exim4
0 upgraded, 1 newly installed, 0 to remove and 197 not upgraded.
3 not fully installed or removed.
Need to get 0B/6354B of archives.
After this operation, 69.6kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package exim4.
(Reading database ... 119558 files and directories currently installed.)
Unpacking exim4 (from .../archives/exim4_4.69-2_all.deb) ...
Setting up exim4-config (4.69-2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-daemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not installed.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

