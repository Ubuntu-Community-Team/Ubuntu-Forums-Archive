---
title: "What is the /.dev directory?"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-03-20
While trying to get my Benq scanner working (I did and then lost it) I ran into a directory (in Warty) that I've never read about :  /.dev. It's filled with a long list of device files, including /usb/scanner0. On the other hand, my /dev directory doesn't list scanner0 or any scanner, though my GUI Device Manager lists my scanner. Can anyone tell me about /.dev?

---

### Post by lorap on 2005-03-21
hi friend!
to check up for device muches your scanner you'd open "/dev" directory and then press on/off button on your scanner watching carefully what devices've appeared/disappeared.
remember one thing,once you get device plugged in but still the power's off the device driver isn't still loaded,but once you've the power on it'd be loaded in "/dev" directory.probably there's another,more beautiful and smart way to find out the device driver you need,but this one's cheap,fast and simple :-)
have a nice day!
pavel

---

### Post by jeremy on 2005-03-21
Does anyone know why my floppy is in /.dev and not /dev?

---

### Post by lorap on 2005-03-21
hi friend!
it's something strange and you know why?
all hided directories in linux are doted i.e. if you wanna get any directory invisible you just create it with dot as the first character.
you'd have directory in /media/floppy.and in /dev you'd have a device called fda or fda0,or fda1.
check if you haven't damaged the system friend.
have a nice day and don't worry,i'd myself reinstalled ubuntu this weak as many as 2 times,but not cause ubuntu's bad but cause i just tried many things.
pavel

---

### Post by David Haas on 2005-03-21
Jeremy--Are you sure that fd0 is just in /.dev? When I did a locate command ($ locate fd0) I saw that fd0 was indeed in /.dev, but was also in /dev.  I don't know the meaning of this. I hope that one of the experts can enlighten you and me about this.

I'd like to know why Ubuntu uses a /.dev directory. Why do they want such a hidden directory, which seems atypical for Linux--at least I've never seen it listed in Linux books? 

Lorap--Thanks for your suggestions about getting my scanner to work, but mine does not have an off/on switch. It's always on, but has a sleep button.

---

### Post by lorap on 2005-03-21
hi again!
then the only thing you've to do just plug it in and unplug watching on devices become visible/invisible.
do it & let me know.
pavel

p.s.:
don't forget you must have /dev being open.

---

### Post by jeremy on 2005-03-22
[QUOTE=David Haas]Jeremy--Are you sure that fd0 is just in /.dev? When I did a locate command ($ locate fd0) I saw that fd0 was indeed in /.dev, but was also in /dev.  I don't know the meaning of this. I hope that one of the experts can enlighten you and me about this.

I'd like to know why Ubuntu uses a /.dev directory. Why do they want such a hidden directory, which seems atypical for Linux--at least I've never seen it listed in Linux books? 

Lorap--Thanks for your suggestions about getting my scanner to work, but mine does not have an off/on switch. It's always on, but has a sleep button.[/QUOTE]
 When I first installed warty last October the floppy didn't work until I changed the fstab entry to read;

/.dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

since then the floppy has worked fine (all I did was add the "." before "dev").

$ locate fd0 shows fd0 as being only in /.dev

---

### Post by David Haas on 2005-03-22
Well Jeremy, the question now is why Ubuntu uses a hidden (/.dev) dev directory. I think we'll need this question answered by one of the Ubuntu developers. But I don't see that it makes any difference to operations once it's found. Your floppy (fd0) in /.dev works fine and i've found that my scanner0, listed in /.dev works fine. However, when Sane at times doesn't recognize that I have a scanner, even though I've listed the path to it correctly as /.dev/usb, I can unplug and then plug it back in to get Sane to open.

---

