---
title: "mount point HDRIVE does not exist"
date: 2009-10-22
forum: Hardware
---

### Post by Bonehead_64 on 2009-10-22
Just to show how bonehead I am I can't even find what Ubuntu I'm running I think it is 8.04 but maybe 8.10. I have a Seacrate 250 Gig that was in an external usb case. It (usb) quit and I know better than try to fix in windoze. On the other hand I haven't used Unix for 19 years and my mind is not what it used to be....

When at:
:~$ sudo mount -t ntfs-3g/dev/sdb1 /media/EXT HDRIVE -o force 

Returns:
mount: mount point HDRIVE does not exist

With the excption of sudo the rest was in an error message, that basically said the drives log says it was not shutdown properly in windoze. I kinda think the space or what ever windoze had there between EXT and HDRIVE did it to me.

T
So I'm sorta asking what now, Ollie?

---

### Post by lloyd_b on 2009-10-22
> **Bonehead_64 said:**
> Just to show how bonehead I am I can't even find what Ubuntu I'm running I think it is 8.04 but maybe 8.10. I have a Seacrate 250 Gig that was in an external usb case. It (usb) quit and I know better than try to fix in windoze. On the other hand I haven't used Unix for 19 years and my mind is not what it used to be....

When at:
:~$ sudo mount -t ntfs-3g/dev/sdb1 /media/EXT HDRIVE -o force 

Returns:
mount: mount point HDRIVE does not exist

With the excption of sudo the rest was in an error message, that basically said the drives log says it was not shutdown properly in windoze. I kinda think the space or what ever windoze had there between EXT and HDRIVE did it to me.

T
So I'm sorta asking what now, Ollie?

Yeah - spaces in directory names causes problems for a lot of commands.  But there's a simple solution: Wrap the parameter with the space in it with quotation marks```
sudo mount -t ntfs-3g /dev/sdb1 "/media/EXT HDRIVE" -o force
```

Lloyd B.

---

### Post by Bonehead_64 on 2009-10-23
> **lloyd_b said:**
> Yeah - spaces in directory names causes problems for a lot of commands.  But there's a simple solution: Wrap the parameter with the space in it with quotation marks```
sudo mount -t ntfs-3g /dev/sdb1 "/media/EXT HDRIVE" -o force
```

Lloyd B.

Thanks, I think I'm done now. I ran the below then again with just "EXT HDRIVE" in quotes with same basic result no such.... So I thought maybe it'll mount from places. Glory be it did, and I can read and play the files in the recycler. The rest of the drive all 232g of it appear empty??? Guess the failure erased all but recycler and system volume info folders. "That's life".

T

sudo mount -t ntfs-3g /dev/sdb1 "/media/EXT HDRIVE" -o force

[sudo] password for thebird: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/EXT HDRIVE: No such file or directory

---

