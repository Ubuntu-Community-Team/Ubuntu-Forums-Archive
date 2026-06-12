---
title: "Can't Upgrade to new Ubuntu!"
date: 2008-10-30
forum: General Help
---

### Post by poo_22 on 2008-10-30
Ok, so i tried to upgrade from the update manager, but i think i had connection problems because it couldnt' download packages. So i got myself a iso of teh new ubuntu release (iso) and followed the instructions here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
for upgrading from cd.
I mounted the iso ok, but i'm not getting a dialogue gox asking for an upgrade, and pressing alt+F2 and running gksu "sh /cdrom/cdromupgrade" doesn't have any effect.

please help!

---

### Post by eternalnewbee on 2008-10-30
Hi there.
Could you be a bit more specific.
Like which iso you downloaded. Did you burn the iso at a low speed?

---

### Post by poo_22 on 2008-10-30
I got Ubuntu 8.10 x86-64 and i mounted it with the mount command, not burn it to cd.

---

### Post by cariboo on 2008-10-30
Where did you mount the iso image? As you can see below I mount mine on /mnt:

```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              15G  4.9G  8.9G  36% /
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  100K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  2.9M  986M   1% /dev
tmpfs                 989M  244K  989M   1% /dev/shm
lrm                   989M  2.4M  987M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6             133G   32G   95G  25% /home
/dev/loop0            698M  698M     0 100% /mnt
```

In my case I would us the command:

```
gksu sh /mnt/cdromupgrade
```

Check to see if you have the iso actually mounted as /cdrom
using:

```
df -h
```

In a terminal.

Jim

---

### Post by poo_22 on 2008-10-31
ok i get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             226G  205G   12G  95% /
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   56K 1003M   1% /dev
devshm               1003M   76K 1003M   1% /dev/shm
lrm                  1003M   44M  960M   5% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      226G  205G   12G  95% /home/phil/.gvfs
/home/phil/Documents/ubuntu-8.10-desktop-amd64.iso
                      700M  700M     0 100% /media/cdrom0
/home/phil/Documents/ubuntu-8.10-desktop-amd64.iso
                      700M  700M     0 100% /media/cdrom0

when i run df -h,
but when i do sudo /media/cdromupgrade it says "sh: Can't open /mount/cdromupgrade"

---

### Post by Elinow on 2008-11-02
Probably, you mounted not an alternate iso image ?

---

### Post by Modarm on 2008-11-02
Hi I have exactly the same issue. I have 3 x Hardy machines and happens on everyone so this is a bug! upgrading should not be so difficult from a CDROM. 

CD is available as shown:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  2.9G   14G  18% /
varrun                316M  100K  315M   1% /var/run
varlock               316M     0  316M   0% /var/lock
udev                  316M   56K  315M   1% /dev
devshm                316M   12K  316M   1% /dev/shm
lrm                   316M   39M  277M  13% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       18G  2.9G   14G  18% /home/nicholas/.gvfs
/dev/scd0             699M  699M     0 100% /media/cdrom0
nicholas@nicholas-desktop:~$ 
The ISO image is direct from the download page. 

Note: its the small things that count!

---

### Post by zvacet on 2008-11-03
```
sudo mount -o loop ~/Desktop/ubuntu-8.04-alternate-i386.iso /media/cdrom0
sudo /media/cdrom/cdromupgrade
```

That should do it.

---

### Post by kurtymckurt on 2008-11-03
One problem i had when trying to run the update from the updatemanager is, i had to run update-manager -d from the command line before it would tell me the update is available. Also make sure all repositories are open under /etc/apt/sources.list  Then try to install the upgrade. This might be more useful then trying to burn off of the iso since all /home will be replaced with new unless you have a seperate home partition.

---

### Post by thestig_992 on 2008-11-03
also make sure youre using the alternate cd (not the live cd), otherwise theres no update script on it

---

### Post by zvacet on 2008-11-04
Command should look 

```
sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0
sudo /media/cdrom/cdromupgrade
```

Sorry for overlook.

---

### Post by scouser73 on 2008-11-04
What I would suggest is that you download the ISO and do a clean installation. I know it's probably what you don't want to do but I always find a fresh install to be the best once I've exhausted all ways of solving an issue.

---

### Post by jimv on 2008-11-04
And make sure you are using the Alternate install CD, not the Desktop cd.

---

