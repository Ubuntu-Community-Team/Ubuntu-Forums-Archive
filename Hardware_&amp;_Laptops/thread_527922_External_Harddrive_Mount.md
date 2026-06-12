---
title: "External Harddrive Mount"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by ascus4 on 2007-08-17
I searched this forum for this and did what I found.  No good.

I purchased a 500gig external harddrive last night / USB interface.

When I plug it in I get the automatic 'what do you want to do' window.  I select open in new window and it then does nothing.  No mount.  When I check for it in media it is not there.

The USB ports do work with other devices.  I have NTFS enabled and am able to read / write my Windows partition on the internal drive.  In NTFS config I do have 'enable write support for external device' enabled.

I tried from terminal: sudo mount /dev/sda1 /home/"username"/external

What should sda1 be?  That may be the problem because it said I needed to specify that.

Please help?

Thank you.

---

### Post by merlinus on 2007-08-17
Check settings in System/Preferences/Removable Drives and Media.

Try mounting it this way:

```

sudo mkdir /media/external
sudo mount /dev/sda1 /media/external -t [SIZE=-1]ntfs-3g -o nls=utf8,umask=0222

```

-merlin
[/SIZE]

---

### Post by ascus4 on 2007-08-19
That mounted the drive and  allowed read access.  
Very cool, thank you.

It did not allow write access.  Possibly a permissions thing, I'll play with it but suggestions are 
welcomed.

Thanks,

---

### Post by dkrepitD on 2007-08-22
you may want to try to use ntfs configuration tool, you can install it from the add/remove Min Menu Item. This should enable you to write to a NTFS Volume.

---

