---
title: "backup tool for large disks"
date: 2008-08-19
forum: General Help
---

### Post by dexter.deepak on 2008-08-19
i need a backup tool,with these requirements of mine :
1. it should be totally free
2. it can be installed and used through windows
3. it should take backups of disks over 250 gb
4. compression is desired.

i am actually fed up of viruses in my dual-boot windows system, and i want something to "clone" my windows partition (250 gb) on a seperate hard-disk, so that i can simply use that backup in a tragedy rather than have a full install.

---

### Post by tuxulin on 2008-08-19
im not really understanding requirement number 2
> 2. it can be installed and used through windows
so ill answer like this.

for cloning your disk then give g4u a try
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/) which is pretty good.

alternatively you could try dd in the command line
make sure you consult your fstab for correct device name
dd if=/dev/rdsk/device-name of=/dev/rdsk/device-name bs=blocksize


for backing up give some time here
[http://www.foogazi.com/2008/02/25/free-linux-backup-solutions/](http://www.foogazi.com/2008/02/25/free-linux-backup-solutions/)

backing up a disk and cloning a disk is not the same thing.

Tuxulin

---

### Post by dexter.deepak on 2008-08-19
> **tuxulin said:**
> im not really understanding requirement number 2



i am sorry for that ambiguity.
actually i want it to be a windows software and not a linux software. i may have to work on a system, where i have no linux installed...so "dd" (which works best on linux for me)  is of no use here.

---

### Post by tuxulin on 2008-08-19
in that case i cant help as most of windows good backup and cloning software are all chargable.. i hope some else my help you out here :)

Tuxulin

---

