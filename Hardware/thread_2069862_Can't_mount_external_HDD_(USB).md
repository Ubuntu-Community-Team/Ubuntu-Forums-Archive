---
title: "Can't mount external HDD (USB)"
date: 2012-10-11
forum: Hardware
---

### Post by Stephan H on 2012-10-11
Hello,

Tried to connect an external HDD (could be NTFS formatted but not sure...).
Can't mount it. Error message goes:

> Beim Zugriff auf „20,2 MiB Wechselmedium“ ist ein Fehler aufgetreten, die Meldung lautet: Die angegebene Operation ist fehlgeschlagen: Requested filesystem type is neither well-known nor in /proc/filesystems nor in /etc/filesystems Ignore the German part but if you search the net for the last part it takes you here:

[https://bugs.archlinux.org/task/23701](https://bugs.archlinux.org/task/23701)

...a missing comma is supposed to be the problem. BUT...I haven't got /etc/filesystems!
So can't do any of these.

Has anyone got an idea?
Would be much appreciated.

Stephan

---

### Post by mikewhatever on 2012-10-11
Arch is oftern not a good source of fixes for Ubuntu, because Arch requires the users to edit config files, whereas Ubuntu usually have stuff pre-configured. 

Looking at /proc/filesystems, here's what I get:
```
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cgroup
nodev   cpuset
nodev   tmpfs
nodev   devtmpfs
nodev   debugfs
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   anon_inodefs
nodev   devpts
        ext3
        ext4
nodev   ramfs
nodev   hugetlbfs
nodev   ecryptfs
        fuseblk
nodev   fuse
nodev   fusectl
nodev   pstore
nodev   mqueue
```

Note that neither FAT nor NTFS are there. 
Which versions of Ubuntu do you use?

On the second thought, you might want to try something suggested [here]("http://forum.ubuntu-it.org/viewtopic.php?f=58&t=466935"):
```
sudo cp /proc/filesystems  /etc
sudo nano /etc/filesystems

```

...and add 
ntfs
vfat

---

### Post by meditatingfrog on 2012-10-11
> **Stephan H said:**
> Hello,

Tried to connect an external HDD (could be NTFS formatted but not sure...).
Can't mount it. Error message goes:

 Ignore the German part but if you search the net for the last part it takes you here:

[https://bugs.archlinux.org/task/23701](https://bugs.archlinux.org/task/23701)

...a missing comma is supposed to be the problem. BUT...I haven't got /etc/filesystems!
So can't do any of these.

Has anyone got an idea?
Would be much appreciated.

Stephan

Are you trying to mount it from the terminal?  Paste the code.  It should be something like:

```
sudo mount -t ntfs /dev/<device> /<path>
```

---

### Post by Stephan H on 2012-10-11
> **meditatingfrog said:**
> Are you trying to mount it from the terminal?  Paste the code.  It should be something like:

```
sudo mount -t ntfs /dev/<device> /<path>
```


...well can't get a device name or path at all. If I click on the device, I get the above mentioned error message.
At some point I get this as well /media/6562-6661/
But no content shown at all. If I copy this into the address bar, it says that this folder doesn't exist.
Terminal also says "not found".
Tried to see it as roon in the terminal but...nothing

---

### Post by Stephan H on 2012-10-11
> **mikewhatever said:**
> Arch is ofter not a good source of fixes for Ubuntu, because Arch requires the users to edit config files, whereas Ubuntu usually have stuff pre-configured. 

Looking at /proc/filesystems, here's what I get:
```
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cgroup
nodev   cpuset
nodev   tmpfs
nodev   devtmpfs
nodev   debugfs
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   anon_inodefs
nodev   devpts
        ext3
        ext4
nodev   ramfs
nodev   hugetlbfs
nodev   ecryptfs
        fuseblk
nodev   fuse
nodev   fusectl
nodev   pstore
nodev   mqueue
```Note that neither FAT nor NTFS are there. 
Which versions of Ubuntu do you use?

On the second thought, you might want to try something suggested [here]("http://forum.ubuntu-it.org/viewtopic.php?f=58&t=466935"):
```
sudo cp /proc/filesystems  /etc
sudo nano /etc/filesystems

```...and add 
ntfs
vfat

Hmm tried this, didn't work. Had vfat before. Now this is my list:

```

odev    sysfs
nodev    rootfs
nodev    bdev
nodev    proc
nodev    cgroup
nodev    cpuset
nodev    tmpfs
nodev    devtmpfs
nodev    debugfs
nodev    securityfs
nodev    sockfs
nodev    pipefs
nodev    anon_inodefs
nodev    devpts
    ext3
    ext4
nodev    ramfs
nodev    hugetlbfs
nodev    ecryptfs
    fuseblk
nodev    fuse
nodev    fusectl
nodev    pstore
nodev    mqueue
                vfat
                ntfs
                fat32
```still wouldn't access the HDD. :(

---

### Post by Bashing-om on 2012-10-11
I'll take a stab at this.
does terminal command :
```
 ls /media/6562-6661/
```return anything ?
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by meditatingfrog on 2012-10-11
> **Stephan H said:**
> ...well can't get a device name or path at all. 

If a device name isn't showing up in /dev/ (as sdb or sdc or something like that), then the problem is beyond the file system.  You should have something show up in /dev/ right after plugging it in.  Maybe try checking the connector/cable.

If it's usb you can try the lsusb command to see if it's showing up there, too, but if it isn't showing up in /dev/ it probably won't show up in lsusb.

Hope this helps.

---

### Post by Stephan H on 2012-10-27
> **meditatingfrog said:**
> If a device name isn't showing up in /dev/ (as sdb or sdc or something like that), then the problem is beyond the file system.  You should have something show up in /dev/ right after plugging it in.  Maybe try checking the connector/cable.

If it's usb you can try the lsusb command to see if it's showing up there, too, but if it isn't showing up in /dev/ it probably won't show up in lsusb.

Hope this helps.

Well, this is what "lsusb" returns:

"Bus 002 Device 004: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge"
It's there...or is it just the bridge device?

I also tried again to add "ntfs" into /etc/filesystems and /proc/filesystems where in both it is missing.
Used "kdesu kwrite" to do it but it wouldn't let me save it, telling me I had no rights. Tried changing the rights under each file's "properties" but there's no active option.

However, I've done ```
cp /proc/filesystems /etc   vi /etc/filesystems/
``` as recommended in [https://bugs.archlinux.org/task/23701](https://bugs.archlinux.org/task/23701)
NTFS shows in /etc but not in /proc and it wouldn't let me add it or do ```
cp /etc/filesystems /proc
```Wondering if this is really the solution...

Stephan

---

