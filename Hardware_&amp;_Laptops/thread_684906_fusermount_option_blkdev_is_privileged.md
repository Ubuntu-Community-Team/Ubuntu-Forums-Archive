---
title: "fusermount: option blkdev is privileged"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by myke on 2008-02-01
I've looked around the forums and checked several ideas how to fix this but to no avail on my system.   Currently using Gutsy Kubuntu.   If I can't fix this latest KDE headache, I may have to move over to Gnome.  I don't like it's looks as much but I hear it's more stable!

Basically what I'm having happen is that when I start my computer with my WD Passport usb portable hard drive, it mounts just fine.  If I want to remove it, I can right click and unmount it fine as well.  The problem comes in when I try to remount it without having to restart the whole machine.  It gives me this error:
> 
fusermount: option blkdev is privileged
FUSE mount point creation failed
Unmounting /dev/sdb1 (WDpassport)

I have full mouting privleges and am in the fuse, sudo, and admin user groups as someone suggested this may help but it still won't work.  I either have to restart from scratch or go to system settings:disk & file systems and remount under administrator login which I coulda just taken the time to restart.   This is simply a pain in the backside that I can't get fixed and didn't crop up until an update in Gutsy a few weeks back.   

I'd really like to just be able to mount my portable drives without having to power down the computer or go thru so many steps to do so.  This should be a simple thing.  I think you could even get drives auto mounted on plugin with Win95 ... which is a sad, sad comparison!!!   :guitar:

btw ... just what is "option blkdev"???   If that is a file permissions problem, where is that file and how to I fix it???

---

### Post by myke on 2008-02-03
any ideas?

---

### Post by Aldoo on 2008-02-10
Maybe some elements here: [http://www.ntfs-3g.org/support.html#useroption3](http://www.ntfs-3g.org/support.html#useroption3)
So check the permissions (suid) of the involved programs (fuse subsystems).
Hope this helps (it just helped me to mount a ntfs partition).

---

### Post by dem0n1c_nerd on 2008-02-19
In addition to being a member of the fuse group I also did this:

chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g)

as mentioned in the given fuse resource.

---

