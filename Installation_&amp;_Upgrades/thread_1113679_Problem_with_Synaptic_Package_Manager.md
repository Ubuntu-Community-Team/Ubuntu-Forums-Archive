---
title: "Problem with Synaptic Package Manager"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by mwhite1206 on 2009-04-01
I was recently trying to install a package, along with its related dependencies (I think I was trying to install vim, but I can't actually remember...) anyway, whilst trying to do this with the Synaptic Package Manager, something went awry and the Package Manager crashed. Now, whenever I try to either start the Package Manager, or install updates off the Update Manager, I get the following error, after which the Manager closes:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried doing as the error said, with the following results:

marc@juju:~$ sudo dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu9) ...
iconvconfig: cannot generate output file: No space left on device

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Writing of cache data failed: No such file or directory
dpkg: subprocess post-installation script returned error exit status 1

I've tried to make space with the apt-get package (eg autoclean, autoremove & clean,) but of those three, only clean runs, whilst the other two throw the same error as the GUI Package Manager. Is this a disk space issue, or is there something else underlying that's stuffed it up?

---

### Post by theozzlives on 2009-04-01
Sounds like your root partition is full, and because of that you have a broken package now. Is there anyway you can resize your root partition, or does it take up the whole disk? If you have a seperate /home, make /home smaller and root bigger.

---

### Post by lykwydchykyn on 2009-04-01
Can you post the output of "df -h"?  That would tell us if it were a disk space issue.

---

### Post by mwhite1206 on 2009-04-01
marc@juju:~/FLASH3.1.1a/source/Simulation/SimulationMain/Jet3D$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda6             2.9G  2.9G     0 100% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M   96K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1006M   1% /dev
tmpfs                1008M  412K 1008M   1% /dev/shm
/dev/sda10             32G  4.6G   26G  16% /home
/dev/sda9             2.9G   70M  2.7G   3% /tmp
/dev/sda8             4.7G  407M  4.1G   9% /var
/dev/sda5              51G   47G  3.5G  94% /media/datawin
/dev/sda2              51G   26G   26G  50% /media/progwin
marc@juju:~/FLASH3.1.1a/source/Simulation/SimulationMain/Jet3D$ 

As you can see, the root partition is quite full, and the home partition is quite not :P how does one go about doing the resizing though? I was actually looking earlier, but couldn't see any built-in partitioning tool...

---

