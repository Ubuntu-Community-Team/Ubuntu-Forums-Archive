---
title: "USB NTFS Hard Disk not mounting...."
date: 2009-08-28
forum: Hardware
---

### Post by sumantagogoi on 2009-08-28
I have an USB hard drive with NTFS filesystem. 
I have used fstab to mount the drive at startup which works just fine.
But during the session if i unplug the drive then the drive cannot be mounted again without rebooting the computer which is a real pain.
Any ideas on how to make it more plug and play and auto mounted whenever the drive is plugged in?????
Also I need full read-write access.

my fstab:```

/dev/disk/by-id/usb-StoreJet_Transcend_10D0758680FF-0:0-part1    /media/Storejet    ntfs-3g    exec,rw,user,umask=000    0 0

```"sudo mount -a" command after unplugging and replugging yields:
fuse: failed to access mountpoint /media/Storejet: Input/output error

---

### Post by sumantagogoi on 2009-08-28
I have found that this is because the USB drive is not automatically unmounted when removed.
I have made a script to do this manually everytime i connect the drive,.
Just wished that it could be done automatically, like in windows.
So if anyone knows please share the knowledge

---

### Post by unc0nn3ct3d on 2010-02-19
Could you share your script with us pretty please?

---

### Post by Ackley19 on 2010-02-19
please share ??

---

