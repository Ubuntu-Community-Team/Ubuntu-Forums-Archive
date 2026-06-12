---
title: "USB flash drive contents show up as garbage"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by roopesh on 2007-04-29
OK I've searched high and low and can't find a reason this is happening: Everytime I insert my USB Flash Drive, it automatically mounts and comes up with garbage for the contents.  See the screenshot attachment, I'm not sure how else to describe it.

I just tested this and it mounts and shows all the data fine in Windows XP.  This has never worked for me.

I'm running Ubuntu 6.10 Edgy.

I'd really appreciate any thoughts as to how to fix this.

---

### Post by earobinson on 2007-04-29
what happens when you do ```
cd /media/usbdisk
ls -la
```

cut and paste the output please

---

### Post by roopesh on 2007-04-29
Wow, that was an impressively fast response.

OK I have no idea what changed (literally, nothing) but now the drive isn't coming up with garbage.  The only thing that's different is that it got mounted on /media/CORSAIR instead of /media/usbdisk.

If it happens again I'll post that output.

Thanks.

---

### Post by earobinson on 2007-04-30
could have been a hw hickup with the computer not having a perfect usb conection to the usbkey hence not able to get the correct name

---

