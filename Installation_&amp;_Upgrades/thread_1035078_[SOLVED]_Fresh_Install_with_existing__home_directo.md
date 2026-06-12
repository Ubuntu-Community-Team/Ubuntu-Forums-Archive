---
title: "[SOLVED] Fresh Install with existing  /home directory"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by snappy46 on 2009-01-09
I am sure that this is probably answered somewhere else but I was not sure what to search for so here we go.

When I first installed Ubuntu a few years back (I think it was ver 6.06) from what I was reading before installation the best directory structure was to have the / (root) on one partition and the /home directory on another partition.  If I remember correctly from what I read this was so that it would allow a fresh install operating system installation on the root.

Ever since my first install I have been using the upgrade function to update Ubuntu with the lastest being 8.10.  After all those upgrades there are a few weird things that seem to happen here and there.  All that just to say that I think that a fresh install would probably be a good thing at this point.

Ok here's my question.  Am I to understand that I can do a fresh install on the / (root) partition and when ask for the /home directory I can just select the one that already exist on a different partition and everything will be ok and that all the software installled on the previous install will still be available???  Will all the software previously installed be automatically reinstalled and all the decrepencies resolved to allow those application to work properly???

Any clarification or link on the process of installing a fresh install of the Operation system ( in this case Ubuntu) and using an already created /home directory (which is presently on a separate partition) would be appreciated.

Thanks

---

### Post by avtolle on 2009-01-09
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion) says it better than I; ignore the title, so to speak, and follow the directions for installing with an existing /home.

---

### Post by tuxxy on 2009-01-09
> Ok here's my question. Am I to understand that I can do a fresh install on the / (root) partition and when ask for the /home directory I can just select the one that already exist on a different partition and everything will be ok and that all the software installled on the previous install will still be available??? Will all the software previously installed be automatically reinstalled and all the decrepencies resolved to allow those application to work properly???

Yes you are correct do the fresh file system install using the / mountpoint and then for your home select your current /home partition and for this select /home as the mountpoint from the dropdown list.

All your settings/files will be saved and available once you login, the software willl need installing again but not configuring so it wont take long.

---

### Post by snappy46 on 2009-01-09
Thank you both for your help.  Let see now if I can do that without screwing anything up.

---

