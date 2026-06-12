---
title: "How do I mount a windows XP hard drive on my Ubuntu 10.04 LTS operating system?"
date: 2010-05-06
forum: Hardware
---

### Post by lukster91 on 2010-05-06
Hello,

I have a computer that has died, and I am trying to recover the files by putting the hard drive in this computer and transfering the files across.

Ubuntu 10.04 won't recognise the hard drive, and I have tried all combinations all coming to the same conclusion. 

Could anyone tell me how I can mount the drive? BIOS/CMOS recognises the drive is there, however I can't boot to it. 

Thanks,

Luke

---

### Post by dabl on 2010-05-06
This is slightly dated (I think ntfsprogs is either included by default or deprecated), but it's basically still good guidance:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

The part about windows is halfway down.

---

### Post by steveneddy on 2010-05-06
An easier way would be to use the Live CD and from the desktop mount both drives and C/P or D&D between them.

---

### Post by lukster91 on 2010-05-09
Thanks for your help, I found installing:

> sudo aptitude install ntfsprogs

...did everything I needed it too. I managed to recover the data.

Thanks!

---

