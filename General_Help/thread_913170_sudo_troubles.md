---
title: "sudo troubles"
date: 2008-09-07
forum: General Help
---

### Post by aaronbp0 on 2008-09-07
I am trying to mount an NTFS drive that didn't shut down successfully, so a dialog box said I have to force it in the terminal. After trying this, I got the message "only root can do that," so I typed "sudo" and then the exact same command. After typing my password, I got the generic usage message that you get if you just type "mount" or if you make a typo. I tried the same command (minus the sudo) in root terminal and the same thing happened.
how do I mount my drive?

---

### Post by lukjad on 2008-09-07
Could you give us the exact output of the command prompt please?

---

### Post by aaronbp0 on 2008-09-07
input:sudo mount -t ntfs-3g /dev/sda2/media/OS -o force

output:Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Sorry it didn't come out formatted... in the edit screen it did.

---

### Post by WRDN on 2008-09-07
Change the command to:

```
sudo mount -t ntfs-3g /dev/sda2 /media/OS -o force
```

You had not put a space between /dev/sda2 and /media/OS

---

### Post by oldos2er on 2008-09-07
If the NTFS drive didn't shut down cleanly, you'll need to run Windows' chkdsk command on it. Ubuntu recognizes NTFS partitions that aren't shut down properly, and refuses to mount them in order to preserve their data.

 "sudo mount -t ntfs-3g /dev/sda2/media/OS -o force" won't work. The correct command would be "sudo mount -t ntfs /dev/sda2 /media/OS," assuming /media/OS exists.

---

### Post by aaronbp0 on 2008-09-07
Thank you! you just saved me about $300 and weeks of my time.

---

