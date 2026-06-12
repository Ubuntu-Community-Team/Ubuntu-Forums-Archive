---
title: "Problem Mounting Ntfs External Drive"
date: 2009-03-05
forum: Hardware
---

### Post by insearchofsomething11 on 2009-03-05
Hi there i'm new to ubuntu and having a problem mounting, or unmounting my ntfs 1000.2 gb external drive.  I had it mounting fine until I accidently unplugged it from my laptop before shut down. Now whenever I try to access it I get a message telling me the volume cannot be mounted: 

$LogFile indicates unclean shutdown (O, O) Failed to mount '/dev/sdbl': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: Choice 1: If you have windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on command line: mount -t ntfs-3g /dev/sdbl /media/disk -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdbl /media/disk ntfs-3g force O O

I inserted 'mount -t ntfs-3g /dev/sdbl /media/disk -o' into the terminal and I got: 
mount: option requires an argument -- 'o'
Usage: mount -V                 : print version
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

I hope someone can help me fix this problem. Thanks in advance.

---

### Post by Fire_Chief on 2009-03-05
> I inserted 'mount -t ntfs-3g /dev/sdbl /media/disk -o' into the terminal

You forgot to put the word force after the -o in the command entry.

Try it with **-o force** in the line.

-Cheers!

---

