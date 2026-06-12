---
title: "No Root File System Is Defined"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Mason Whitaker on 2009-05-16
Trying to install Ubuntu on my Dell Inspiron 1525, but I keep getting an error message stating "No Root File System Is Detected".

Any thoughts? O_o

---

### Post by taurus on 2009-05-16
Did you do the Manual partition?  How did you install it?

---

### Post by Mason Whitaker on 2009-05-16
Just the regular Install application on the Live CD

---

### Post by taurus on 2009-05-16
When you get to the partition screen, which option did you pick?  Are you planning to install Ubuntu along-side windows (dualboot)?

---

### Post by Mason Whitaker on 2009-05-16
In chronological order...

> Opened Install Application on LiveCD Desktop
> English Automatically Selected, Forwarded
> America Automatically Selected, Forwarded
> Keyboard Output USA Automatically Selected, Forwarded
> Starting up Partitioner...
> Blank space where partitions are to be shown
> Forwarded anyways
> Message, "No Root File System Is Defined. Please Correct This From The Partitioning Menu"

---

### Post by taurus on 2009-05-16
It means the installer couldn't detect your harddrive.  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That would be a lower case letter L, not number 1.

Is there anything (like windows) on that harddrive?

---

### Post by Mason Whitaker on 2009-05-16
> **Terminal Command Results:**
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS

> **taurus said:**
> Is there anything (like windows) on that harddrive?Windows Vista Ultimate, would that be the cause of the problem? If so, how would I go about deleting Vista from my harddive?

---

### Post by taurus on 2009-05-16
Do you want to install Ubuntu on the harddrive, using the whole disk, wiping out windows?

---

### Post by Mason Whitaker on 2009-05-16
> **taurus said:**
> Do you want to install Ubuntu on the harddrive, using the whole disk, wiping out windows?Of Course :popcorn:

---

### Post by Hobgoblin on 2009-05-16
Start the partition manager manually and delete the windows partition, then try the install again.

---

### Post by Mason Whitaker on 2009-05-16
GParted isn't letting me edit my /dev/sda1 entry O_o

---

### Post by taurus on 2009-05-16
Post the screenshot (Applications -> Accessories -> Take Screenshot) of gparted.  

Otherwise, use gparted to delete /dev/sda1.  Then, create a new partition, /dev/sda1, that takes up the whole harddrive and format it to ext3.  Save it and run the installer again.

---

### Post by Mason Whitaker on 2009-05-16
[IMG]http://img407.imageshack.us/img407/4903/screenshotfnk.png[/IMG]

There you go kind sirs

---

### Post by taurus on 2009-05-16
You have /dev/sda1 mounted to /cdrom!  What's the output of this command from a terminal?

```
df -h
```

---

### Post by Mason Whitaker on 2009-05-16
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 490M  2.7M  487M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 490M  2.7M  487M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 490M     0  490M   0% /lib/init/rw
varrun                490M  108K  490M   1% /var/run
varlock               490M  4.0K  490M   1% /var/lock
udev                  490M  148K  490M   1% /dev
tmpfs                 490M  600K  490M   1% /dev/shm
rootfs                490M   54M  436M  11% /
/dev/sda1             112G   39G   74G  35% /cdrom
/dev/loop0            674M  674M     0 100% /rofs
tmpfs                 490M  156K  490M   1% /tmp

---

### Post by taurus on 2009-05-16
How about if you unmount /dev/sda1 first and then run the installer again.

```
sudo umount /dev/sda1
```

---

### Post by Mason Whitaker on 2009-05-16
Couldn't unmount...

umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by taurus on 2009-05-16
Did you boot Ubuntu from a CD or did you run it from windows?

---

### Post by Mason Whitaker on 2009-05-16
I used unetbootin, but I didn't think that would cause any problems o_O

---

