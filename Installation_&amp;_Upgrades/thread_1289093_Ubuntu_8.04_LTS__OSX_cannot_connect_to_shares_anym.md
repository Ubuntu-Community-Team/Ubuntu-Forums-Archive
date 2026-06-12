---
title: "Ubuntu 8.04 LTS : OSX cannot connect to shares anymore"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by lptr on 2009-10-12
Last week we had an Samba update in 8.04 LTS. Of course I did an update. 

As I am not regulary using Samba shares with my Mac I did recognize it today. When connecting to Samba server through Finder I cannot see any shares nor cannot connect to it. There are no messages in logs - it simply does nothing. 

Strangely XP workstation (running inside a virtual machine on exact the same Mac) still is working as before. Seems in this update something did break the functionality for Mac smb clients. Weird :( ...

[sorry] forgot to mention: Mac is running under OSX 1.5.8; Samba under LTS 8.04 is version 3.0.28a. And - yes - of course everything worked before I applied the update.


[update -> solved]
OSX had some troubles with its own firewall as it seems. I could not exactly find out what was wrong. This morning box nerved with other mad things. Thunderbird could not connect to Internet, Firefox - same. After rebooting system things went normal. This is one of the disadvantages of any machine sleep modes - or in other words - seldom rebooting systems.

rob*

---

