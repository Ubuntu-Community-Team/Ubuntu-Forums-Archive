---
title: "Windows on extended partition - grub fail"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by rahulthewall3000 on 2009-03-22
Hello,

Over the weekend, I installed Ubuntu for a friend. However, his windows is on an extended partition. Roughly, the partition table looks like this:

```
/dev/sda1 - Extended
/dev/sda3 - Swap [Primary]
/dev/sda4 - Linux [Primary]
/dev/sda5 - Windows [Logical]

```The grub entry is like this:

```

title Windows XP Professional
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,4)
makeactive
chainloader +1

```However, it just fails to boot, fails with the message device not recognized or something similar.

Any help would be appreciated.

Thanks
Rahul

---

### Post by meierfra. on 2009-03-22
It sounds like you deleted or formated the partition containing the boot files for XP.

Have a look at this tutorial:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

After you restored the boot files, you will have to use 

partition(3)

in boot.ini and

title Windows XP Professional
rootnoverify (hd0,4)
chainloader +1

in menu.lst.


If you need more help, post the output of "sudo fdisk -lu"

---

### Post by rahulthewall3000 on 2009-03-26
Thanks, that solved it!

---

### Post by meierfra. on 2009-03-26
> Thanks, that solved it!
Good news. Keep up your good work spreading Ubuntu.

---

