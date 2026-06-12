---
title: "Problem with my HDD"
date: 2009-01-29
forum: Hardware
---

### Post by kacper00100 on 2009-01-29
Hi Im totally new to Ubuntu, and I have a problem. I bought an external HDD a few months ago (when I still had Windows) but now that I´ve changed to Ubuntu Im having some problems with it. At first it worked fine but then I started mucking around with it (as usual). So, eveytime I try to plug it in it gives me this error:
```
Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

AND:
```
Cannot mount volume.

Unable to mount the volume 'MEDIA'.

mount_point cannot contain the following
characters:newline, G_DIR_SEPARATOR (usually /)
```

I think I know what I did wrong but could someone explain to me how to fix this please.

Thanks

---

### Post by dabl on 2009-01-29
Without seeing your /etc/fstab file, I can only guess that you have some problem with the name(s) you have chosen for a mount point.  Linux doesn't like spaces and some non-alphanumeric characters in some places, including the names of devices and mount points.  So, here are some examples of "good" mount points -- perhaps you can rename yours to something like this:

/media/docs
/media/pix
/media/music
/media/disk1
/media/sdcard
/media/mystick
/media/12345

:)

---

### Post by kacper00100 on 2009-01-29
Ye thats what I´ve been trying to do but I don´t know how because its not there in ´properties´ anymore

---

### Post by dabl on 2009-01-30
> **kacper00100 said:**
> 

its not there in ´properties´ anymore

???

Open the console window and ```
cat /etc/fstab
``` to see the file.

Use ```
sudo mount
``` to see currently mounted partitions.

Use ```
gksu gedit /etc/fstab
``` to edit the file with root privileges.

Use ```
sudo mount -a
``` to remount all partitions shown in /etc/fstab.

---

### Post by neophytepwner on 2009-03-03
I am having a similar problem.  I just installed Ubuntu since windows crashed.  I need to access files on my external HDD through linux but I don't know how to mount the drive.  I just figured out how to use terminal, but I may need a step by step walk-through editing /etc/fstab to mount the drive as it seems is necessary.  
Thanks for your help

---

