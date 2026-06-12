---
title: "NTFS:  resetting $LogFile so that ubuntu will mount"
date: 2008-07-12
forum: Hardware
---

### Post by RascalHoudi on 2008-07-12
Hi all.

Using an external NTFS USB harddrive that gets moved between different machines.

The issue I run into is that when the drive is disconnected from a windoze box without the proper 'remove device' routing being done, then ntfs marks the disk as dirty and ubuntu doesn't want to mount it.

Known Solutions
1) Take the usb drive back to a windows box, mount it, then unmount it properly.  Ubuntu is then happy to see it, welcomes it in, gives it a beer and they have a great time together.  This can however be a problem if I don't have a windows box handy at the time....

2) Clean the $LogFile in ubuntu.  I am able to do this by doing a mount with a force option... 
(e.g.  
sudo mount -t ntfs /dev/sdb1 /tmp/mntpoint -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.)

Now that the $LogFile dirty flag is cleared, I umount it, unplug/replug my usb cable and it mounts under /media/drivelabel and I'm good as gold again.


Here's my question:
-is there a simpler way of resetting the $LogFile, and then having the usb mount point activated without resorting to unplugging the usb cable?




I am building this laptop for my daughter to take to university (the last thing I want is to have her run windows on networks which are sure to be vulnerable to lots of download cowboys pulling in all kinds of viruses).
Since I'm going to be a few hours away, I want to eliminate little issues like this.   Any ideas will be appreciated.

thx.

---

### Post by matt$2 on 2008-07-12
Yes there should be a way.  Considering the log is cleared, if ubuntu's system were to reassess from scratch, it should mount it happily; amounts to unplugging and replugging.

Try repeating the boot up process that probed and created and mounted devices.  I'm in Windows atm so I can't see what the standard system files are, but do try

   sudo devd

That should do it.  Otherwise go to /etc/init.d and try restarting the matching service that deals with hardware;  notably hotplug or coldplug.

Post results.

---

