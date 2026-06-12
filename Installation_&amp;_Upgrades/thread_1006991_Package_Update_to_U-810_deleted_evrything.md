---
title: "Package Update to U-810 deleted evrything?"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by SlowJet on 2008-12-09
Hey guys!

I did a usually weekly update to U-8.10 in VBox.
Using synaptic manager.
It download the package lists (a bunch)
Then it said it had to remove some and install 7,   blah blah blah 
before it could continue.
It then started deleting everything.
Network, openoffice, kernels,
finally it errored out or it would have delete over 1 GB.

What is happening with this?
I've updated this a dozen times without a problem.

Ouch!

SJ

---

### Post by bapoumba on 2008-12-10
Did you get it sorted out?

---

### Post by SlowJet on 2008-12-13
NO, I recovered the backup of the VDI and updated again from the Nov 24 VDI and got the same 39 packages as before.
The update today shows none available.
I'll wait a week and see if there are any then.

SJ

---

### Post by bapoumba on 2008-12-13
Please post your sources.list, but I suppose it will be ok since you have already upgraded before:
```
cat etc/apt/sources.list

```

Did you manually run an update beforehand ? If the update does not go correctly on startup, sometimes the package manager is not properly synched with the repos.
```
sudo apt-get update
sudo apt-get dist-upgrade
```
(dist-upgrade upgrades the whole distribution and not only individual packages, and thus checks deps and other things more carefully).

---

