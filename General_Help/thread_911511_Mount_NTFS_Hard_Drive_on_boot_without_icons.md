---
title: "Mount NTFS Hard Drive on boot without icons"
date: 2008-09-05
forum: General Help
---

### Post by darkhammer8108 on 2008-09-05
Im trying to mount 2 NTFS hard drives to my home directory on boot but i dont want the desktop icons to show up for these drives. however i want icons to still show up on the desktop for everything else (ie. external ntfs drives, usb flash drives, fat partitions). how do i make it so the desktop ignores these two drives exclusivly?

EDIT: these are the lines in my fstab
```
/dev/sdb1	/home/shaun/Errinok	ntfs-3g	users,uid=shaun,gid=shaun,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/sdc1	/home/shaun/Errinna	ntfs-3g	users,uid=shaun,gid=shaun,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
```

---

### Post by Scunge on 2008-09-05
Perhaps the fact that it's in your home directory is causing it to "automagically" put the icons up for you.

There was a topic about this already somewhere, I'll edit this post if I find it, but what I said last time was to mount the partitions out of "/media" (in that case) and then the icons won't automatically come up. Perhaps try the same thing here, like use a "/volumes" directory or something.

Then you can perhaps do ```
ln -s /volumes/Errinok
``` in your home directory and see if they don't come up then, while still giving you access where you've set it up already.

Edit: [**[color=blue]There we go![/color]**](http://ubuntuforums.org/showthread.php?t=898739) A few more options for you to try as well.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by darkhammer8108 on 2008-09-06
thanks that did it. what i had to do was mount it into /mnt and make sure the uid,gid and fmask/dmask were set correctly so only i had access to the files. thanks a bunch for the help :-)

---

