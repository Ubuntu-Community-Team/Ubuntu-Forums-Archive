---
title: "secondary disk controller failure !"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by Tarmatt on 2006-10-11
Hello

I had a problem after a reboot:

```
 1792 secondary disk controller failure 
```

I pressed F10 for going into the menu but a blue box appeard asking me a code I don't have. I pressed two times "enter" and ubuntu launched itself.

Before this successfull launch, i tried to boot from the ubuntu cd-rom but the message was the same, so i reboot again.

This problem came after a little problem with my cd-rom device (i think), i was reading an audio cd with soundjuicer and i opened the device without stopping anything. As a result, i had an unstoppable process and a zombi one, both from soundjuicer. I could'nt "kill" them.
Then, i was froze... no mouse, no keyboard. Manual boot and the failure message.

I work on a HP compaq nx7010
kernel 686
ubuntu dapper drake

here is my fstab:
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks for your help

---

### Post by Tarmatt on 2006-10-11
I forgot to add that i can't mount any cd now...

---

