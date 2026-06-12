---
title: "Can't write to external hard drive"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by turtlepaul on 2007-02-04
I have a 3.5 external hdd made by US modular. My computer recognizes the drive and I've had no problems with copying data from it, but when I tried to back something up it wouldn't let me. I went to 'permissions' to see if I could change it but it said I couldn't because it is a read-only disk. I've never had a problem with this hard drive on Windows. Can I fix this?

---

### Post by taurus on 2007-02-04
You can't write to it because it's mounted as root.  Therefore, you need to use the sudo command if you want to write stuff to it but if you want to move stuff there, then you have tu unmount it and mount it again with the right permission!  What's the output of this command from a terminal with the drive connected (and mounted) to your machine?

```
df -h
```

---

### Post by turtlepaul on 2007-02-04
> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              78G   52G   22G  71% /
varrun                252M   80K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  164K  9.9M   2% /proc/bus/usb
udev                   10M  164K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/sdf1              49G   26G   24G  53% /media/Paul
/dev/sdf2              49G   18G   32G  35% /media/Jack
/dev/sdf3              55G  181M   52G   1% /media/usbdisk


That's the output. So what exactly do I do to be able to write to it?

---

### Post by Dritzen on 2007-02-04
If the drive is NTFS formatted, then Ubuntu will mount it read-only by default because the NTFS driver is in beta.  There are guides on how to install and use the beta NTFS driver but you have a chance of destroying the data on the drive.

Mounting it read only is fine.  It won't damage the drive just by accessing the data.

If the data is valuable, you can connect the external drive to a Windows computer and access the drive via samba.  That's what I do.  I can write to the drive, delete, etc, without worrying about destroying the data.

---

### Post by turtlepaul on 2007-02-04
So can I write to a NTFS filesystem at all or do I have to have another one. I still have plenty of unallocated space on the hard drive. What should I format it as? 

Oh and taurus, you said something about a sudo command that would allow me to write to the hd?

---

### Post by turtlepaul on 2007-02-07
Ok, I downloaded a ntfs driver, but now I can't mount the drive. The data wasn't too valuble so it's ok if it's lost (unless something happens to my computer too). What should I doo to make it so I can back stuff up on the hard drive?

---

