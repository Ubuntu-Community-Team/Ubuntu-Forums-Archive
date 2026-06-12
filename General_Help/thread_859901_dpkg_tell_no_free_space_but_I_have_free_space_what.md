---
title: "dpkg tell no free space but I have free space what's happened? :("
date: 2008-07-15
forum: General Help
---

### Post by v.mazzotta on 2008-07-15
I've same problem.
I installe ubuntu 8 server.

After i attemp to install ubuntu-desktop

Download all for 40 minutes and when arrived to final print an error message and execute:

sudo dpkg --configure -a

I execute command and go out /var/lib/dpkg/status no space left on device.

So I verify and isn't corret.

I execute df -h and you can see that have free space:

Filesystem         Size         Used     Avail  Use%     Mounted on
/dev/sdc1          233G       1,5G     220G  1%            /
varrun             1007M      184K    1007M  1%           /var/run
varlock            1007M           0    1007M  0%           /var/lock
udev               1007M        72K   1007M   1%           /dev
devshm           1007M           0    1007M   0%           /dev/shm
/dev/sdc5          4.7G        4.0K     4.7G   0%           /FAT32

I execute sudo fdisk -l and print follow:

Device boot   Start      End       Blocks               Id  System
/dev/sdc1            1      30394     244139773+   83   Linux
/dev/sdc2     30395      32339      15623212+    82   Linux swap / Solaris
/dev/sdc1     32340      32947        4883760+     5   Extended
/dev/sdc1     32340      30394        4883728+     b   W95 FAT32

Where is the problem?

I test to execute:

sudo apt-get clean all
or
sudo apt-get clean
or
sudo dpkg --configure -a


Without results always same message go out:
dpkg: failed to open '/var/lib/dpkg/status' for writing status information: No Space left on device.

I search in google but normally problem is free space, but in my case I've free space.

Somebody can help me?

Kind Regards
Vincenzo

---

### Post by iaculallad on 2008-07-15
Create the backup of the original file:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-old.original
```

Then, copy /var/lib/dpkg/status-old as /var/lib/dpkg/status:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

And;

```
sudo apt-get update
sudo dpkg --configure -a

```

---

