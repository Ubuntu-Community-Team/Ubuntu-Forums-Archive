---
title: "upgrade 7.10 to 8.04"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by mjern92 on 2009-05-19
I am trying to upgrade 7.10 to 8.04.  The update manager fails.  I looked at the /var/log/dist-upgrade/main.log file and see the below.

2009-05-19 18:38:51,421 ERROR IOError/SystemError in cache.update(): 'Failed to 
fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz) 
404 Not Found [IP: 91.189.88.45 80]

I know Gutsy hit EOL and is not in the archive.ubuntu.com folder, but the update manager is searching there.

What do I need to do to do the upgrade from 7.10 to 8.04?

---

### Post by Sef on 2009-05-19
You could try [upgrading this way]("https://help.ubuntu.com/community/HardyUpgrades") or  [upgrading this way]("https://help.ubuntu.com/community/EOLUpgrades").   For the former, go down to "
[B]Upgrading Using the Alternate CD/DVD"

[/B]Howerver, the best way is to do a clean install.

---

### Post by mjern92 on 2009-05-20
Neither of those ways worked for me.  They both give errors.

The first gives the error that I listed.

The second gives this error

[I]Could not calculate the upgrade 

A unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 
[/I]

---

### Post by mjern92 on 2009-05-21
I figured it out.   I followed steps similar to that shown in bug 264181 chaning feisty to hardy,  and was able to upgrade.

---

