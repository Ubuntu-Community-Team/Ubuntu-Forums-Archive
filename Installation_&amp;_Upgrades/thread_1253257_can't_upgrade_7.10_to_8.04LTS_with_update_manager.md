---
title: "can't upgrade 7.10 to 8.04LTS with update manager"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by jazrav on 2009-08-29
I have been using Ubuntu 7.10 for some time now and am unable to upgrade to 8.04 LTS with update manager.  I get the following error messages:

[I]Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug.

[/I]And after closing this window i get:

[I]Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

[/I]Has anyone had a similar problem and managed to resolve it?

(I need to upgrade as I am unable to install mySQL in this version...)

---

### Post by mikewhatever on 2009-08-30
Ubuntu 7.10 had reached it's end of life sometime in April 2009. The repositories are gone, which explains the message. It's not really a bug.
Anyway, I don't know if there is a way to upgrade an unsupported version, perhaps a reinstall is in order.

---

### Post by raymondh on 2009-08-30
[https://help.ubuntu.com/community/EOLUpgrades#7.10%20to%208.04%20(Gutsy%20to%20Hardy](https://help.ubuntu.com/community/EOLUpgrades#7.10%20to%208.04%20(Gutsy%20to%20Hardy))

Hope this helps.

---

