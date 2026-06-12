---
title: "Install partiton problem"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by birdkathe on 2009-01-31
Hi,

I'm trying to re-install Ubuntu (Heron) I've installed from this cd before so I'm pretty sure the cd is fine.

I'm running into issues with the partition finder. Apparently I have no partitions to install on. I am not partitioning the drive and have no other OS installed on this machine. I'm reinstalling because the most recent update bricked my box and this seemed to be the most straight forward solution.

Help?
-Kathe

---

### Post by taurus on 2009-01-31
You mean the installer doesn't detect your harddrive?  From the LiveCD, open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
free -m
df -h
```

---

### Post by boof1988 on 2009-01-31
Is there a "Guided - use entire disk" option like in the attached screen shot?  If there isn't, I'm not sure what to do.

---

### Post by Mookinator on 2009-01-31
i'm getting the same error with Ubuntu Studio 8.10. Just sits there every time. BIOS can see the drive fine, but the installer won't find the drive.

my Ubuntu 8.04 installer seems to be working fine.

~Mike

---

### Post by birdkathe on 2009-02-02
Sorry for the slow response, hopefully someone is watching this thread :)

Here is what I get:
```

$sudo fdisk -l
<no response>
$free -m
          total    used   free   shared   bufferes   cached
Mem:      7998      732    7266      0        78       349
-/+ buffers/cache:  303    7694
Swap:         0       0       0
$df -h
Filesystem    Size  Used Avail Use% Mounted on
tempfs        4.0G   13M   3.9G 1%  /lib/modules/2.6.24-19-generic/volatile
tempfs        4.0G   13M   3.9G 1%  /lib/modules/2.6.24-19-generic/volatile
varrun        4.0G  100K   4.0G 1% /var/run
varlock       4.0G   4.0K  4.0G 1% /var/lock
udev          4.0G    64K  4.0G 1% /dev
devshm        4.0G    12K  4.0G 1% /dev/shm
tempfs        4.0G    16K  4.0G 1% /tmp
gvfs-fuse-deamon  4.0G 32M 3.9G 1% /home/ubuntu/.gvfs

```

Help?
-Kathe

boof1988: no such luck on the "Guided - use entire disk" option.

---

### Post by birdkathe on 2009-02-02
Not sure if this is useful:

```

$sudo gparted
====================
libparted: 1.7.1
====================
Unable to open /div/scd0 read-write (Read-only file system). /dev/scd0 has been opened read-only
Unable to open /div/scd0 read-write (Read-only file system). /dev/scd0 has been opened read-only
Unable to open /dev/scd0 - unrecognised disk label

```

gparted is then empty when it opens.

---

### Post by taurus on 2009-02-02
Reboot and go into the BIOS and see if your harddrive is still listed.

---

### Post by birdkathe on 2009-02-02
Not quite sure that this is what you mean but:

```

Boot menu
==Select a Boot First drive ==
Floppy
LS120
Hard Disk
 -Bootable Add-in Cards
SATA-CDROM
<more divices ZIP& USB & LAN>

```

I have also been poking around the log files when I try to install. I'm getting the following in the 

/var/log/messages
```

...
Feb 3 00:01:50 ubuntu kernel: [    0.00000] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO

```

I get a similar error when I try to run gparted

-Kathe

---

### Post by taurus on 2009-02-02
There should be another option that says something about Device in the BIOS.  Boot option/menu just lets you pick which device you want to boot first when you first turn on your machine.

---

### Post by birdkathe on 2009-02-02
Ok, sorry that took me a while to figure out how to get in to the BIOS. I honestly haven't poked around in here before so I'm not sure how to recognize if there is a problem here.

In the Standard CMOS Features page it only looks like the CD (Serial ATA 2 Channel: TSSTcorp CDDVDW SH-S) is recognized.

What am I looking for here?

-Kathe

---

### Post by taurus on 2009-02-02
I don't know what model and manufacture you have so I can't really you the layout but when you first get into the BIOS, take a picture and post it here.  Sure somebody would have seen it before and tells you which option to move (with arrow keys) to see if the BIOS still detects your harddrive.

---

### Post by birdkathe on 2009-02-03
Here are a couple of shoots of the BIOS screens. I noticed that the ATA channel 1 is now occupied when it wasn't yesterday, still bricked though.

-Kathe

[IMG] http://lh6.ggpht.com/_dhkHWMHZL-4/SYjclvOfhTI/AAAAAAAAB0A/9IHrjgieiec/s144/IMG_1085.JPG[/IMG]

[IMG] http://lh4.ggpht.com/_dhkHWMHZL-4/SYjcYVR6_WI/AAAAAAAABz8/TsDHM6Don3c/s144/IMG_1084.JPG[/IMG]

---

