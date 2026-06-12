---
title: "ubuntu alternative from USB probs"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by junke1990 on 2009-08-24
hey guys 

I'm trying install the alternative version from usb, but it isn't working. I cant get the usb mounted like a cdrom drive or what so ever.

I've posted a full report about what I did yesterday but no responds...
[http://ubuntuforums.org/showthread.php?t=1247987](http://ubuntuforums.org/showthread.php?t=1247987)

I tried everything that's online, mounting in others way replacing the initrd and kernel but still no luck. 

could it be that I boot the usb installer from kboot with the following line

```
kexec ubnkern --initrd=ubninit --append="root=/dev/sda1" -f
```

should the --append="root=/dev/sda1" be a problem if I try to mount it again later on to /cdrom?

---

### Post by stlsaint on 2009-08-24
srry i havent put ubuntu on the ps3 yet but have you checked the site for specific instructions on this?

---

### Post by junke1990 on 2009-08-24
nobody knows! there are solutions everywhere.... and the all say the opposite of each other.

I tried the Ubuntu 8.04 not working... so 9.04 ps3 edition and that one gets stuck as soon as the GUI is loaded (that is if you make it to there) 

The problem for me is I dont have a cd burner anymore, I have a eee 1000h. Great for work and travel but in this case...

---

