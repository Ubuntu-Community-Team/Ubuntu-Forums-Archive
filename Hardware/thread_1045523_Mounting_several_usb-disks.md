---
title: "Mounting several usb-disks"
date: 2009-01-20
forum: Hardware
---

### Post by Bartje on 2009-01-20
Hi all, 

I've got several external hard drives (usb-disks), and on one of them I have some music. I'd like to let amarok, or rhythmbox play its contents whenever I want. The only problem is, when I start the usb-disks in a different order, they switch mount-points and Amarok, or Rhythmbox doesn't find the music anymore.

Is there a way to tell ubuntu to mount which drive at exact the same mount-point each time the drive starts, so the order of starting is not important anymore? It is quite annoying to notice you can't listen to your music, and have to restart the external drives (I've got 4) because you didn't start them in the same order.

greets,
Bart

---

### Post by cariboo on 2009-01-20
If you have the usb rives connected all the time, you can automatically mount them using fstab eg:

```
#/dev/sdb1
UUID=0160b7ed-810e-45e9-9a23-2d54e36aeff3  /home/backups  ext3	  relatime	0  2
```

I use the above command in /etc/fstab to mount an external usb drive to /home/backups on my server.

Jim

---

### Post by Bartje on 2009-01-20
thanks, but a little more explanation could help. What is this UUID, a unique identifier for the harddrive? If so, how can I find it for my drives?

---

### Post by taurus on 2009-01-20
Make sure it is plugged in.  Then run

```
sudo blkid
```

---

### Post by Bartje on 2009-01-20
I don't have the drives with power on all the time of course, I only put them on when I need them. The usb-cable is connected all the time though.
I see you commented the /dev/sdb1. Is this to prevent it looking to the device, and to let it look directly for the UUID?

If I'm right about the UUID as the unique identifier for the usb-drive, how come it isn't implemented into Ubuntu to let it mount the usb-drives to the same mount-point each time it gets connected? I mean, it's such a 'user-friendly' approach that it should be implemented.

thanks for your help already.

greets,

Bart

---

### Post by Yashiro on 2009-01-21
You can right click mounted drives and set the mount points from the properties menu.

---

