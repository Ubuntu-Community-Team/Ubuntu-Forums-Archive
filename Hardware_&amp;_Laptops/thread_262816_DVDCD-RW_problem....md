---
title: "DVD/CD-RW problem..."
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by tvtalkshowshigh on 2006-09-22
i've recently upgraded the cd-rom drive in my dell latitude c610 to a dvd-rom/cd-rw combi drive. CDs work fine, as they did with the old drive but while DVDs apear to mount, i can't actually read the files. I can navigate the directory structure, and even read smaller files (ifo, bup) but if i try to open or copy and vob file off the disc i get an I/O error.

this is the fstab entry for the drive:
```
/dev/hdc   /media/cdrom0   udf,iso9660   user,noauto   0   0   
```

as far as i can tell it's mounting fine, so i don't think that's the problem. I also don't think it's a permissions problem since i can get to other files on the disc.

it has just occured to me that this may be something to do with the way ubuntu reads video dvds; do i need a specific library just to pull vob files off a video dvd disc? i'll see if i can get hold of a data dvd to check if it's just video discs with the problem. in the mean time, does anyone have any thoughts?

thanks in advance.

---

### Post by tvtalkshowshigh on 2006-09-24
i just tried a data dvd and that works fine, so it's something specific to video dvds. does anyone know what i need to have installed for video dvds to work properly?

thanks.

---

### Post by xyz on 2006-09-24
[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") is one way of doing it. See if it works for you.

---

### Post by tvtalkshowshigh on 2006-09-24
thanks xyz. i had a bit of a scout around and realised that libdvdcss2 is not installed by default due to copyright/patent stuff. it's now installed and dvd video playback is perfect. thanks!

---

