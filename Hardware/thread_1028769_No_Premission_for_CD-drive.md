---
title: "No Premission for CD-drive"
date: 2009-01-02
forum: Hardware
---

### Post by penguinchrissy on 2009-01-02
When ever I try and play a movie on my laptop I get the message

Could not open location; you might not have premission to open this file.

I'm the only one who uses this laptop and this is kinda annoying how can I fix it?

---

### Post by doas777 on 2009-01-02
I've had the same problem in past, but usually it was because I locked mount down to root only with Bastille. 

can you load the disk with:
```

sudo mount /dev/scd0 /media/cdrom0

```
?

---

### Post by penguinchrissy on 2009-01-02
Ok I did sudo umount /dev/scd0 /media/cdrom0 first to unmount it then remounted it the way you told me I get this
block device /dec/scd0 is write-protected, mounting read-only. Then when I try and do anything it just does nothing but sit there. Opening movie player the disk isn't being read at all and then I have to force quite the program. 

I also got this which is why I unmounted it. 

mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: accourding to  mtab, /dev/scd0 is already mounted on /media/cdrom0

This is a fresh install of 8.10

---

