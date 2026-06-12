---
title: "thumb drive is read-only?"
date: 2008-06-12
forum: Hardware
---

### Post by wendallsan on 2008-06-12
Hi everyone, I have a USB thumb drive that I've been using for some time that has suddenly become read-only.  It is format to FAT, 2GB in size.  This worked fine last time I stuck it in the machine.  It mounts automatically and I can read from it, but I can't write to it.  I don't see any mention of it in my /etc/fstab (not sure if it should even be there since this isn't a 'permanent' disk), and in /etc/mtab I see:

/dev/sdg1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

What can I do to make this disk writable again?  Thanks for any help you can give.

---

### Post by wendallsan on 2008-06-21
Alright, I tried something and now can't mount the thumb drive as read-only even:

I right-clicked on the mounted volume and found a way to change permissions, there were 2 permissions listed under 2 seperate settings (I think these settings were fmask and dmask, but I can't get back to this window now that I've changed them).  Both settings were 0077.  I tried changing these to umask values I recognized: '777'.  Now when I jam the drive into my computer I get the error: 

Cannot Mount Volume.

The volume uses the fmask=777 file system which is not supported by your system.

Is there any way I can undo this?  I'm guessing it might want '0777' instead of '777', but of course have no way to get back to this window to change the values.  I don't see anything relating to this in my fstab or mtab files.  Any help?

---

### Post by Bubba64 on 2008-06-22
You can reformat it with gparted.

---

### Post by wendallsan on 2008-06-22
Awesome, reformatting it worked.  Thanks a million!

---

### Post by Bubba64 on 2008-06-22
I had a similiar problem glad it worked.

---

