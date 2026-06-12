---
title: "Help! Upgrading to 8.10"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by freechiru on 2009-10-04
Following [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) .  Cannot update though Update Manager; cannot set Software Sources to show short-term upgrades -- no "Release Upgrades" tab.  Cannot update via ISO CD; netbook has no CD drive and command given for virtual CD drive not allowed.  What do I do?

---

### Post by Jimmyfj on 2009-10-04
If you run this command in a terminal:

```
sudo update-manager -d
```

You'll get the upgrade running.

---

### Post by slakkie on 2009-10-04
Try the following:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade

```

---

### Post by freechiru on 2009-10-04
Thanks for the help.

@Jimmyfj: That brings up my Update Manager, yes, but it doesn't see any new updates (at all, let alone version updates) to install.

@slakkie: I tried that; the first code worked (although what exactly did it do?  It asked me for permission to remove 8 packages) but when I ran the second code I got "No new release found."

If it changes anything, I'm running Netbook Remix; my current version according to lsb_release -a is:

```
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.2
Release:    8.04
Codename:    hardy
```

---

### Post by slakkie on 2009-10-10
edit the file /etc/update-manager/release-upgrades as root

Change Prompt=lts to Prompt=normal.

Then redo the do-release-upgrade command.

The first bit actually installed the do-release-upgrade command.

If you wait a little over 6 months (April 2010), you will be able to upgrade directly to 10.04. 9.10 comes out in Oct 29 and then they start working on the next LTS version. 

I also read some changelogs that they made it possible to upgrade from hardy to karmic (9.10) directly. Maybe wait for that package to hit hardy and you can make a huge leap forward. You would now need to upgrade first to 8.10, then 9.04 and then 9.10 and 6 months later to 10.04.. I would advise to wait a bit, less hassle :)

---

### Post by freechiru on 2009-10-29
slakkie,

I tried those commands, but I still come up with "No new release found" -- which is odd, given that Karmic is released today.  (Also, apologies for not trying this sooner; I decided to give up and wait until Karmic was released, but that isn't working either, it seems.)

For the record, my system hasn't found any updates for the last 25 days.  I suspect that's bad...?

---

