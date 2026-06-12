---
title: "External HD Won't Mount"
date: 2009-03-01
forum: Hardware
---

### Post by dobber1978 on 2009-03-01
Ok, new to Linux, using the Ubuntu platform and I can't mount my external HD

Basically I plug it into the USB and I get the error message

First Error:

Cannot mount volume
Unable to mount the volume
Details
$logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdf1'; Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action; Choice 1: If you have Windows then disconnect the external device by clicking on the safely remove hardware icon in the taskbar then shutdown windows then you can use the force option for your own responsibility. For example type the command line: mount -t ntfs -3g /dev/sdf1/media/disk -o force Or add the option to the relevant row in the /ect/fstab file: /dev/sdf1/media/disk ntfs-3g force 00

Second Error

Unable to mount 80.0 GB Media
DBus error.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible cause include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken.

Hopefully I copied those error messages over properly

Ok, those were the two errors, I tried to fource the mount as per Error 1 and it did not correct anything, keeps telling me: Mount: Only Root Can Do That

Not sure what this root is?

Can anybody explain? Have a solution?
Thanks
Jeff

---

### Post by taurus on 2009-03-01
Make sure you include the sudo in front of the command to get root privilege.

```
**sudo** mount -t ntfs-3g /dev/sdf1 /media/disk -o force
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kestrel1 on 2009-03-01
Before running the command above type```
sudo mkdir /media/disk
```

---

### Post by dobber1978 on 2009-03-01
And all the sudo command does is giving root privilege??

What are root privileges?

---

### Post by dobber1978 on 2009-03-01
So I tried the sudo infront and it still does not work

Here is the copy from the terminal

jeffery@jeffery-desktop:~$ sudo mount -t ntfs-3g/dev/sdg1/media/disk -o force
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
jeffery@jeffery-desktop:~$ 


Any other recommendations?
Thanks

---

### Post by BbUiDgZ on 2009-03-01
> **dobber1978 said:**
> Ok, new to Linux, using the Ubuntu platform and I can't mount my external HD

Basically I plug it into the USB and I get the error message

First Error:

Cannot mount volume
Unable to mount the volume
Details
$logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdf1'; Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action; Choice 1: If you have Windows then disconnect the external device by clicking on the safely remove hardware icon in the taskbar then shutdown windows then you can use the force option for your own responsibility. For example type the command line: mount -t ntfs -3g /dev/sdf1/media/disk -o force Or add the option to the relevant row in the /ect/fstab file: /dev/sdf1/media/disk ntfs-3g force 00

Second Error

Unable to mount 80.0 GB Media
DBus error.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible cause include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken.

Hopefully I copied those error messages over properly

Ok, those were the two errors, I tried to fource the mount as per Error 1 and it did not correct anything, keeps telling me: Mount: Only Root Can Do That

Not sure what this root is?

Can anybody explain? Have a solution?
Thanks
Jeff

plug the drive into a windows machine and use the safely remove usb drive wizard thingy (next to the clock)to unmount the ntfs partition cleanly. then it will mount in ubuntu

ntfs is not native to linux

---

### Post by dobber1978 on 2009-03-03
Thanks, that seemed to work with the plug it into a windows machine first and then try it on the Ubuntu,

---

### Post by kestrel1 on 2009-03-03
> **dobber1978 said:**
> And all the sudo command does is giving root privilege??

What are root privileges?
Root privileges is similar to administrator in Windows, so the sudo command just elevates your privileges on what you are trying to do.

I can see why the command never worked for you```
sudo mount -t ntfs-3g/dev/sdg1/media/disk -o force
```
There should be spaces in some places & you have none. It should have read```
sudo mount -t ntfs-3g /dev/sdg1 /media/disk -o force
```
I know this is all academic now, but thought I would point it out as a matter for future reference.

---

