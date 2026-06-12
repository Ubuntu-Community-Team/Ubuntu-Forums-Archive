---
title: "Remove 1GB limit on Pendrive installation"
date: 2008-10-31
forum: General Help
---

### Post by Alaric on 2008-10-31
I recently went out and bought an 8G flashdrive and used usb-creator to install Ibex on it, but it works just like a liveCD and that's presented a problem.  I can't accomplish any upgrades because "E: You don't have enough free space in /var/cache/apt/archives/." When I run a df -lh I get: 

```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  104K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1005M   1% /dev
tmpfs                1008M  120K 1008M   1% /dev/shm
rootfs                124M  118M     0 100% /
/dev/sdb2             6.1G  1.3G  4.9G  21% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1008M   28K 1008M   1% /tmp
/dev/sda5              44G   29G   13G  69% /media/disk

```

Any ideas on how to remove the 1G cap on the filesystem sizes?

---

### Post by dcstar on 2008-10-31
> **Alaric said:**
> I recently went out and bought an 8G flashdrive and used usb-creator to install Ibex on it, but it works just like a liveCD and that's presented a problem.  I can't accomplish any upgrades because "E: You don't have enough free space in /var/cache/apt/archives/." When I run a df -lh I get: 

```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  104K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1005M   1% /dev
tmpfs                1008M  120K 1008M   1% /dev/shm
rootfs                124M  118M     0 100% /
/dev/sdb2             6.1G  1.3G  4.9G  21% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1008M   28K 1008M   1% /tmp
/dev/sda5              44G   29G   13G  69% /media/disk

```

Any ideas on how to remove the 1G cap on the filesystem sizes?

8.10 has installing a Live system onto a USB built into it, I suggest you use that tool as it works fine (I have a 4GB "casper-rw" partition on my USB stick install along with a 4GB FAT32 partition).

---

### Post by Alaric on 2008-10-31
Then what on Earth is usb-creator included in Ibex for if it's not the program of which you speak?

---

### Post by Jose Catre-Vandis on 2008-12-15
I have come up against the same problem when trying to customise my live usb stick (Xubuntu 8.10). Is there no way of increasing the size of the main file system to allow for additional packages to be installed? I have already cleaned out the archive but am only allowed to install 44m of packages at one go.

[EDIT] Ignore me, I am an idiot! My 1GB stick was just not big enough to cope with the size of installed packages I required. Have moved up to a bigger stick and am now doing fine. If it helps others to check the space they have available, they should run the command
```
df -lh
``` in a terminal and look for the entry "rootfs". This tells you how much space you have / have left. It may also make sense to create a separate partition on your flash drive for files so that these can be accessed outside of the virtual filesystem (casper-rw) when simply using as a flash drive and not a live usb stick.

If you want to customise your live usb stick then you should make the persistent drive as big as you can. For my Xubuntu 8.10, I have a 1GB persistent drive, and after the base installation of additional software (codecs, restricted-extras, flash, java etc) this leaves me with @ 500mb to play with.

---

