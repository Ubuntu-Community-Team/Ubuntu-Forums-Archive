---
title: "Cannot &quot;eject&quot; a USB hard disk"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2007-04-27
I have a USB hard disk which I use with my Dell Inspiron 8600 laptop running Ubuntu Feisty.

The disk is detected fine but I cannot eject it.  Right-clicking on the drive icon on the desktop and selecting "Eject" results in an error message:

[i]There is data that needs to be written to the device HTS42121 2H9AT00 before it can be removed.

Please do not remove the media or disconnect the drive.[/i]

I cannot think what data this could be as I am not interacting with the drive in any way and the message does not go away with time.  My guess might be that the disk was incorrectly disconnected at some point and this has left behind an error.

Can anyone suggest how to solve the problem?

Incidentally, if it's relevant, the disk is formatted with ext3 filesystem.

Many thanks,

     -- Joe

---

### Post by lw5 on 2007-04-27
This is not a direct solution, but doesn't 'sudo umount /dev/[UsbDiskNameHere]' work?

---

### Post by nrfool on 2007-04-27
I noticed similar thing. When you are on the desktop, you can only eject (which doesn't work well with usb drives, since the computer can't really eject them). However, if you are in a file manager, you can right click the icon on the side bar and choose "unmount".

---

### Post by alexgenaud on 2007-04-30
As suggested, 'sudo umount' should work. For those less familiar with the devices, you can most likely use the /media (mount point), which will have the same name as displayed on the desktop. So from the command line:


sudo    umount    /media/MyUsbDrive

Password: MyUserPassword


Known Bugs:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/36252](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/36252)
[https://bugs.launchpad.net/ubuntu/+bug/108205](https://bugs.launchpad.net/ubuntu/+bug/108205)

---

### Post by scanez on 2007-04-30
Try my suggestion in this thread: [http://ubuntuforums.org/showthread.php?p=2474560#post2474560]("http://ubuntuforums.org/showthread.php?p=2474560#post2474560"). Note also that this will give the option "Unmount" instead of "Eject" when you right click on the drive.

---

### Post by spier on 2007-04-30
This may be just a dumb adwise, but i experienced same issues while trying to eject usb memory keys. I noticed that my dapper install got the wrong permissions to /usr/bin/pumount. Following suggestions from these forums, I got it working after running 

```
 sudo chown root:plugdev /usr/bin/pmount && sudo chmod 4710 /usr/bin/pmount
```

---

### Post by ericmarceau on 2007-04-30
Since the priviledges are set for root, and the user is something else, then the devices won't be writeable/readable.

Instead of working with plugNplay, which won't give full control on the device mount point, I work through the
   /etc/fstab
and use a set of scripts I've created for mount/dismount USB/Optical/Other drives.

I post them here for reference.

If anyone can improve on them or generalize them further, I would appreciate getting a copy, but I hereby put any copyright claim on these into public domain.


Eric

---

### Post by lixy on 2007-05-04
> **scanez said:**
> Try my suggestion in this thread: [http://ubuntuforums.org/showthread.php?p=2474560#post2474560]("http://ubuntuforums.org/showthread.php?p=2474560#post2474560"). Note also that this will give the option "Unmount" instead of "Eject" when you right click on the drive.

Brilliant! It worked like a breeze (or should I say a feist?).

I confirm that a regular "sudo umount /media/InsertDiskNameHere" works but Nrfool's workaround doesn't.

Thanks a lot!

---

