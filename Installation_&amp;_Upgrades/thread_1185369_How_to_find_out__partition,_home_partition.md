---
title: "How to find out / partition, /home partition?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-12
Installing Jaunty on top of an upgrade to Jaunty (which had lots of problems).

When I originally installed Ubuntu (Hardy) I failed to make a note of which partition was assigned to /, /boot, /home, /tmp, /usr, /var, etc.

I can boot to the Jaunty live CD and also to "rescuecd".  Both of these have file browsers (like Nautilus) and I can mount and unmount drives and partitions and see the files on them.

It is a dual boot machine (Jaunty + XP).  All the windows stuff is on 2 hard drives, and Jaunty is exclusively on the 3rd hard drive.  Jaunty file systems are ext3 (except /swap which is linux-swap).

For the hard drive with the Ubuntu installation, is there a way that I can determine which partition was assigned to /, which to /home, which to /usr, etc.?

Thanks in advance!

---

### Post by kimda on 2009-06-12
df -h or mount on the commandline 

or use gparted in Gnome.

---

### Post by raymondvillain on 2009-06-12
If I use gparted, where will it show the mount points of a particular partition?  I have fired up gparted and I can see the partitions (/dev/sdc10, /dev/sdc11, /dev/sdc12, /dev/sdc5, etc.) but cannot figure out, say, if /dev/sdc5 was mounted as /boot, or /tmp, or whatever.

thanks for your suggestion

---

### Post by kimda on 2009-06-12
The mount command in the terminal shows you exactly which partitions are mounted and on which mount points they are mounted.

---

### Post by dstew on 2009-06-12
There is no information in the partitions themselves as to what mount points they might have been mounted to in the past, so that information is not available to gparted. If you boot a Live CD, for example, you can mount /dev/sdc5 to /media/disk or anywhere you want, as long as the mount point exists in the currently running system. But, when you unmount the partition, the partition itself has no memory of where it was mounted to. It becomes available to be mounted anywhere you want it to go.

The mount point information for an Ubuntu system is stored in the /etc/fstab file that is created when you install Ubuntu. If you can access this file from your original Hardy installation, it will list the file systems and the mount points. It would normally be on the partition that was originally the root parititon. Mount the various partitions and look for the /etc directory, and you should be able to find fstab. However, if it is not there, or has been overwritten by your attempted Jaunty install, or is empty, the next best thing would be to look at the root directories of each partition. Usually you can figure out what they were by which files and directories are there. For example, the partition formerly mounted at /boot will contain the grub directory.

---

### Post by raymondvillain on 2009-06-12
Thank you dstew!

That was exactly what I needed.

Do you have any idea why Nautilus would not start in Jaunty, or from the Jaunty live CD?  I can start it when I boot to the Hardy live CD, but not Jaunty.

Thanks again for your info.

---

### Post by dstew on 2009-06-12
How are you trying to start Nautilus? Usually I just go to the Places menu.

EDIT: Googling around, I found a [bug report]("https://bugs.launchpad.net/ubuntu/jaunty/+source/brasero/+bug/335942") for this. This command fixed it for one user:```
sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
```Try it on your hard-disk Ubuntu Jaunty boot.

See [this too]("http://blog.ibeentoubuntu.com/2009/04/awful-nautilus-brasero-bug-in-jaunty.html").

---

### Post by raymondvillain on 2009-06-12
I start Nautilus just like you do, the "Places" menu.  I'm going to re-boot now, re-install Jaunty, and if Nautilus does not work I'll try that bug fix you found.  Thanks for pointing it out to me.

I do have 32 bit Jaunty on an older machine with a pentium 4.  Both of which facts appear as culprits in the bug report.  Hopefully this will solve the problem.

---

