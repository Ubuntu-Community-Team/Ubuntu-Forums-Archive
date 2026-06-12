---
title: "Installing Arch Grub Error 22"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by JK3mp on 2009-04-27
Well title says it all trying to setup Arch linux for a friend( already hav it on mine) and some reason i get Grub Error 22. Didn't have to do much with my config, don't know why i can't figure this out. For more detailed info on it. head to [my arch linux post]("http://bbs.archlinux.org/viewtopic.php?pid=544030") where i got some of them workin on it but no luck yet. THought maybe someone here could help out. Thanks.

---

### Post by JK3mp on 2009-04-27
*bump* :-(

---

### Post by Sub101 on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Should fix it.

---

### Post by JK3mp on 2009-04-27
> **Sub101 said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Should fix it.

Thanks i'll try it out and let ya konw how it goes . :)

---

### Post by JK3mp on 2009-04-27
No luck. Plus im bootin off a live arch cd (FYI), but first wouldn't find stage 1 and then wouldn't mout to mnt/root.

---

### Post by JK3mp on 2009-04-27
*bump* :(

---

### Post by Sub101 on 2009-04-27
Sounds to me like its not been installed properly. If you boot from a live cd are any files installed?

---

### Post by JK3mp on 2009-04-27
Well it lets me navigate around a bit anywho.. if thats what you mean. Also read my Arch Forum posts linked above to see what i tried, exactly how i installed it (partition and grub setup) etc. That'll probably help if you think its my own error.(which it likely is)

---

### Post by JK3mp on 2009-04-27
*bump*(sorry, very impatient, lol)

---

### Post by Herman on 2009-04-27
```
#(0) Arch Linux
title Arch Linux [boot/vmlinuz26]
root (hd0,2)
kernel /vmlinuz26 root=/dev/sda**3** ro
initrd /kernel26.img

#(1)Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```Try with 'root=/dev/sda3' and see if that helps.

I'm only guessing, it that doesn't help you then please post your fdisk output. I'm not sure of the command for that in Arch.
In Ubuntu it's 'sudo fdisk -lu'.
That information and/or the output from 'sudo blkid' is almost needed when considering boot loader problems.
EDIT: Oh, sorry, you already posted it in the other forum,
```

Name-------Flags-------Type----------FSType------------------Label---------------------size
---------------------------Pri/Log ------Freespace ----------------------------------------1.05
sda1 ---------------------Primary------Unknown-----------------(27)--------------------8856.2
sda2 -----Boot-----------Primary---------NTFS ------------------[^R]-------------------156266
sda3--------------------- Primary---------Linux-------------------------------------------84933

```

---

### Post by JK3mp on 2009-04-27
Sorry forgot to mention that i already did that, just neglected it in the code on arch forums, :(. my bad.  And i'll get right on the fdisk output.

---

### Post by SuperSonic4 on 2009-04-27
```
#(0) Arch Linux
title Arch Linux [boot/vmlinuz26]
root (hd0,2)
**kernel /vmlinuz26 root=/dev/sda3 ro**
initrd /kernel26.img

#(1)Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```

I think you need to put in the disc UUID there and make sure it has the right root of course 

```
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/<uuid> ro

```

```
ls -lF /dev/disk/by-uuid/
``` will give the UUID.

You may be able to put 

```
#(0) Arch Linux
title Arch Linux [boot/vmlinuz26]
root (hd0,2)
**kernel /vmlinuz26 root=/dev/disk/label/sda3 ro**
initrd /kernel26.img

#(1)Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```

---

### Post by JK3mp on 2009-04-27
Okay mirrored fdisk -lu best i could...

```

Disk /dev/sda : 250.0gb
255 HEADS 635 SECTORS/TRACKS, 30401 CYLINDERS
TOTAL 488397168 SECTORS
UNITS=SECTORS OF 1*512=512 BYTES
DISK IDENTIFIER, 0X0F7F14E6

DEVICE____BOOT_____START___________END__________BLOCKS___ID__SYSTEM
-----------------------------------------------------------------------------
/dev/sda1/         2048            17299455     8648704  27 Unknown
/dev/sda2/ *       17299456        322507111    142603528 7 HP/NTFS
/dev/sda3/         322507112       48839204     82942476+ 83  Linux

```

Hope it helps someone figure this mess out.

---

### Post by JK3mp on 2009-04-27
> **SuperSonic4 said:**
> ```
#(0) Arch Linux
title Arch Linux [boot/vmlinuz26]
root (hd0,2)
**kernel /vmlinuz26 root=/dev/sda3 ro**
initrd /kernel26.img

#(1)Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```

I think you need to put in the disc UUID there and make sure it has the right root of course 

```
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/<uuid> ro

```

```
ls -lF /dev/disk/by-uuid/
``` will give the UUID.

You may be able to put 

```
#(0) Arch Linux
title Arch Linux [boot/vmlinuz26]
root (hd0,2)
**kernel /vmlinuz26 root=/dev/disk/label/sda3 ro**
initrd /kernel26.img

#(1)Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```

Not entirely sure what you mean but here's the output of ls -lF /dev/disk/by-uuid/

```

lrwxrwxrwx 1 root root 10 2009-04-27 04:50 6A02839A02836A41 --> ../../sda1

lrwxrwxrwx 1 root root 10 2009-04-27 04:50 AC1C474E1C4712AE --> ../../sda2

```

---

