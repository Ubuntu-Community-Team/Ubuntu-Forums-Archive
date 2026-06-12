---
title: "cdrom must be umounted before eject"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by dabear on 2005-06-01
Hi, I just wondered, why the heck do I have to umount ("umount /dev/cdrom"
) my cd-/dvd player before I can press the eject button on the drive it self? Ok, so I can just find the drive on the desktop- and press eject on it, but that's not what I want to do. How do I solve this?

---

### Post by thrift on 2005-06-01
This is "just the way it works" in Ubuntu.  If you want to get around this look into using subfs with the automounter, or install a kernel with supermount available.  Then you can eject just by hitting the button.

---

### Post by neighborlee on 2005-06-03
[QUOTE=thrift]This is "just the way it works" in Ubuntu.  If you want to get around this look into using subfs with the automounter, or install a kernel with supermount available.  Then you can eject just by hitting the button.[/QUOTE]

This is not true I'm rather sure of it..I read the warty wiki which said clearly that a 'fix' needs to be done for 'umount,eject' and they mention mandriva and suse whom use either supermount/submount respectively...

any idea if this is still being considered ??


thx
nl

---

### Post by pb7804 on 2005-06-04
I have experienced something like that. More to say, I was unable to eject media at all even after successful unmounting thru gnome gui. There was error messages about invalid argument or something. Then I just typed ```
sudo eject -v -s /dev/hdc
``` and only this did the trick, but error message was displayed anyway:
```
eject: trying to eject `/dev/hdc' using SCSI commands
eject: SCSI eject failed
```

Then I've discovered that I can't read any files on any CD media I mount, all discs appeared just blank.

Well, I don't like the idea of rebooting every time to use another disc...

---

### Post by pb7804 on 2005-06-04
Finally, it works!

First I've enabled SCSI emulation as described in wiki [*How To Enable SCSI Emulation With Hoary Kernel 26*](http://www.ubuntulinux.org/wiki/HowToEnableSCSIEmulationWithHoaryKernel26),
then I slightly modified **/etc/fstab** from what was recommended in wiki to allow unmounting/ejecting not only to root:

```
/dev/scd0  /media/cdrom0  udf,iso9660  ro,user,noauto,**umask=000**  0  0
```

The last thing that would made me happy is enabling all this to work transparently by pressing eject button on the drive...

---

