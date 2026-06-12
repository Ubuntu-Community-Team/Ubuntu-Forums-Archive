---
title: "Clie/Palm Kontact sync problem"
date: 2005-11-18
forum: General Help
---

### Post by martamius on 2005-11-18
I am having trouble setting up kpilot to sync to kontact. kpilot downloads all the data from my clieNX73V correctly, and i can see them all in kpilot just fine. however, when I try to sync to kontact, i get the following errors in my logs:
> 
KPilot HotSync log, Fri Nov 18 12:59:59 2005
Version: KPilot 4.6.0 (blivit)
Version: pilot-link 0.11.8
Version: KDE 3.5 (RC1)
Version: Qt 3.3.4
12:59:59  KPilot 4.6.0 (blivit) HotSync starting...
12:59:59  Using encoding UTF-8 on the handheld.
12:59:59  [File Installer]
12:59:59  No Files to install
12:59:59  [Internal Editors]
12:59:59  Databases with changed records: 
12:59:59  Databases with changed flags: 
12:59:59  Databases with changed AppBlock: 
12:59:59  Could not find conduit abbrowser_conduit.
12:59:59  Could not find conduit knotes-conduit.
12:59:59  Could not find conduit vcal-conduit.
12:59:59  Could not find conduit todo-conduit.
12:59:59  Could not find conduit mal_conduit.
12:59:59  Could not find conduit sysinfo_conduit.

I never had this problem with hoary.

I have also tried installing kitchesync,  but it doesn't seem to be functional, and i can't find any documentation for kitchensync either.
 anybody else having this problem?
any idea how to fix it? 
Thanks.

---

### Post by Sokraates on 2006-11-01
I've tried for hours to get Kontact and my Palm Tungsten E to sync, but to no avail. Although, interestingly, contacts were synced to Kontact, but not back to my palm. First, if you have a fresh install of edgy, install kdepim and then you can try again.

You might also need multisync, but simply installing it won't work, because libmultisync-plugin-palm won't install, since a dependency is missing and that can't be fixed. [This](https://launchpad.net/distros/ubuntu/+source/multisync/+bug/67520) is the bug-report. 

I installed libpisock8 from dapper (you'll find it at packages.ubuntu.com), then installed libmultisync-plugin-palm, but Kontact still won't sync.

After that I even installed evolution, imported everything from kontacted and tried to sync. And along came another known bug: gpilot doesn't find  the palm, if it's connected by USB. 

Appart from kontact, syncing works great.

Well, should you manage to make it work with kontact, please tell me how.

---

