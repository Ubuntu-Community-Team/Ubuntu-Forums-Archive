---
title: "What happens to grub on upgrade to windows 7"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by djuliette on 2009-05-04
I currently dual boot between vista and Ubuntu.  If I upgrade vista to windows 7 rc will it wipe out my grub menu?  I'm thinking to just upgrade vista not install windows 7 along side of it.  And if it does wipe out grub how easy is it to recover?

---

### Post by ptn107 on 2009-05-05
You should be fine as GRUB chainloads vistas/7s bootloader.

---

### Post by caljohnsmith on 2009-05-05
Yes, installing Windows will overwrite Grub in the MBR (Master Boot Record), but you can easily recover Grub by following these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Let me know how that goes or if you run into problems.

Cheers,
John

---

### Post by djuliette on 2009-05-05
Thanks John,  I upgraded to windows 7 rc and easily recovered GRUB with all my settings intact.

Thanks.

---

### Post by caljohnsmith on 2009-05-05
Great, glad to hear your upgrade to Windows 7 RC went OK and that you can still dual-boot using Grub. Cheers and enjoy your OSes. :)

John

---

### Post by indiekid97 on 2009-05-11
After following the instructions listed, 
```
>find /boot/grub/stage1
```
<br />
```
>find /grub/stage1
```

return 
```
Error 15: File not found
```

Is there another way I can determine the location of the MBR so I can reinstall?

Note:
My normal Ubuntu partition is mounted as /media/disk and contains the /boot/grub/stage1 file, however, my LiveUSB drive does not.

Thanks to everyone or the help.

---

### Post by gamblor01 on 2009-05-11
indie,

Boot up with a live cd and then paste the output of the following command:

```

sudo fdisk -l

```

We should be able to tell from that which partition Ubuntu is installed on, and therefore where grub resides (unless you have multiple Linux partitions).

---

### Post by indiekid97 on 2009-05-12
Thanks for the reply,
running 
```
fdisk -l
``` 
wouldn't allow me to see the partition tables of my main drive (sda) for some reason (it reported that the drive was "BUSY")

After my initial panic, I was able to deduce my partition table by mounting the partitions to /mnt/root as suggested [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and using 
```
hdparm -z
```

Although finishing that method did not work for me,  was able to use your method to reinstall after I knew that Ubuntu was on sda4

All in all, thank you for pointing me in the right direction! It's amazing how quickly I can be reduced to a newbie when confronted with things I've never had to deal with.

---

### Post by gamblor01 on 2009-05-12
> 
After my initial panic, I was able to deduce my partition table by mounting the partitions to /mnt/root as suggested [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Ha awesome.  Their suggestion was just to try all possibilities until you find the right one.  Nice.

As long as it worked I suppose that's all that matters, but the fact that fdisk couldn't read the partition table would trouble me (if it were my box).  You might want to start backing up your important files to DVD, another hard drive, etc.  Better safe than sorry.

---

### Post by indiekid97 on 2009-05-12
It worried me too, but it reads them just fine when running Ubuntu from the HD, so I let it be.
Plus, I have a triple redundant backup of important files. Paranoia can be helpful sometimes :P

---

