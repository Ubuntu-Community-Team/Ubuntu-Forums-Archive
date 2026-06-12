---
title: "Read Only File Error"
date: 2008-10-03
forum: General Help
---

### Post by jman24 on 2008-10-03
Hi, I'm trying to put music files on my nokia n810, which I hook up to my computer via USB. The problem is that I can't create file in it's harddrive because of the read only property. I tried right clicking on the drive-properties- and then enabling read and write, but when I check the preferences again it's back to ---. I also trying the nautilus method, by going to terminal and trying to change the preferences from there, still no show. How can I place these music files on the hard drive for the n810, which seems to be read only?

Thanks

---

### Post by ajmorris on 2008-10-03
> **jman24 said:**
> Hi, I'm trying to put music files on my nokia n810, which I hook up to my computer via USB. The problem is that I can't create file in it's harddrive because of the read only property. I tried right clicking on the drive-properties- and then enabling read and write, but when I check the preferences again it's back to ---. I also trying the nautilus method, by going to terminal and trying to change the preferences from there, still no show. How can I place these music files on the hard drive for the n810, which seems to be read only?

Thanks


Hi there,
to be able to copy files to your device as a normal user, you may need to re-mount the device manually with -o rw . And you can edit your /etc/fstab to alter the mounting process permanently. However, with your current automatic hotplug mount, you should be able to copy the files to it fine, as a root user.

AJ

---

### Post by jman24 on 2008-10-03
Hey I tried to paste something to the drive and I still get the error: The destination is read only. Are there any solutions?

---

### Post by ajmorris on 2008-10-03
try this:
```
sudo su
```
```
mount -o rw /dev/<device> /media/<mount point>
```

and see if you can copy to it, also what file format is the phone?

AJ

---

### Post by jman24 on 2008-10-04
haha, it's not a phone, I always get that. It's a pda type thing. The format is umm...vfat FAT32

---

### Post by jman24 on 2008-10-04
Yikes, I tried that above and it still wouldn't paste. But I did get this in the terminal, by the way I'm a beginner, and am not that experienced with terminal commands etc.

Here was the response I got from terminal








root@Computadora:/home/user# root@Computadora:/home/user# mount -o rw /dev/2.1 GB Media/media/disk-1
bash: root@Computadora:/home/user#: No such file or directory
root@Computadora:/home/user#  mount -o rw /dev/disk-1/media/disk-1
mount: can't find /dev/disk-1/media/disk-1 in /etc/fstab or /etc/mtab
root@Computadora:/home/user#  mount -o rw /dev/2.1 GB Media/media/disk-1
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



Thanks for your help by the way :)

---

### Post by ajmorris on 2008-10-04
ah, no you need to mount the actual device, and the mount point you use, has to be already there...

so, can you run the following please :)
```
sudo mkdir /media/nokia
```
and post the output of this:
```
sudo fdisk -l
```

AJ

---

