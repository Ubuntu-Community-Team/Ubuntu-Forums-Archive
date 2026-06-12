---
title: "Samsung YP-MT6 Incorrect Free Space"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by jazzbert on 2007-05-14
Using Ubuntu 7.04
Hardware: Samsung YP-MT6 - USB-connected MP3 player
Brief Problem Description: Linux system shows significantly less space than is actually available

I'm having a problem with my Samsung YP-MT6 MP3 player.  When I connect it to my Ubuntu 7.04 system via USB, it automatically mounts; however, it does not show the correct free space.  Additionally, I cannot add files to it beyond the free space it indicates.  The amount of free space seems unpredictable (at least I haven't figured out the pattern) but it always shows less free that the device shows for itself or that appears when I connect it to a Windows PC.

I've searched Google and several forums, but the closest answers I've found are a hidden ".TRASH" folder (which I can't see in Nautilus or via ls -l command) and a permissions issue (as far as I can tell chmod is 777 on the device folder...but I could be looking in the wrong place.

I'm a Windows "pro" and Linux "newbie" trying to make the jump using Ubuntu...  any help is appreciated.

-Jazz

---

### Post by jazzbert on 2007-05-15
P.S.  Here's my /etc/mtab entry for this device:
```
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1001,utf8,umask=077 0 0

```

-Jazz

---

