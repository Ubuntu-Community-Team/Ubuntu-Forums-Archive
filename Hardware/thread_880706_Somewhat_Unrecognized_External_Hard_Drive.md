---
title: "Somewhat Unrecognized External Hard Drive"
date: 2008-08-05
forum: Hardware
---

### Post by raywood on 2008-08-05
I have a Rosewill external SATA drive enclosure containing a 750GB Seagate.  It is connected by USB cable to my primary computer.  In Ubuntu, I go into File Browser and double-click on this drive, which is named OFFSITE.  I get an error message:

Cannot mount volume.
You are not privileged to mount the volume 'OFFSITE'.

If I right-click and select Properties > Basic, I get this:

Name:  OFFSITE
Type:  Unknown Type
Location:  computer:///
Volume:  Unknown
MIME type:  application/octet-stream

Modified:  unknown
Accessed:  unknown

Properties > Permissions gives me "The permissions of "OFFSITE" could not be determined."

If I examine the drive using System > Administration > Partition Editor, I see it as /dev/sdd5, ext3, 698.64 GiB.  Right-clicking > Information yields Status:  Not mounted.

If I switch the drive to my secondary computer, also running Ubuntu, File Browser shows the contents of the drive as being lost+found.  Right-click > Properties > Basic says 35.1 GB used, 652.5 GB free, along with other information, and Permissions says I am the owner and my access is "Create and delete files."

My question:  how come one computer can see it and work with it, and the other can't?

---

### Post by phidia on 2008-08-05
Quick answer: examine your /etc/fstab file and I'm betting the computer that recogizes the drive has an entry for it. I could be wrong though-but that's the first thing that comes to mind. 

What filesystem do you have on that drive anyway? Usually ubuntu will automount your plug in drives.

If my guess is wrong open a terminal, with the drive plugged in, and enter > sudo fdisk -lu. You can do that on both computers and compare the differences.

---

### Post by tamoneya on 2008-08-05
open a terminal with the drive plugged into to the first computer and run this:```
sudo mkdir /media/external
sudo mount /dev/sdd5 /media/external
```

---

### Post by raywood on 2008-08-06
That worked.  But it went away when I rebooted.  Do I have to enter that second line each time I reboot?

---

### Post by evets25 on 2008-08-06
the first line creates a directory for the drive to be mounted to, the second actually mounts it. ("mount" is the command, "/dev/sddd5" is the drive, and "/media/external" is the directory it is being mounted to.)  In order to have this happen every time you boot, you need to add an entry for this drive to your /etc/fstab file. If you don't, then you'll need to run that second command every time you reboot, in order to remount the drive.

---

