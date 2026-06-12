---
title: "Running a DiskCheck on SD Media Card"
date: 2009-04-13
forum: Hardware
---

### Post by Max Avion on 2009-04-13
Hello, 

I have been having some trouble with my blackberry being able to read the data on my SD Media Card. I found that someone had posted the same issue on this forum:[http://ubuntuforums.org/showthread.php?p=6330827&highlight=fsck+-a#post6330827](http://ubuntuforums.org/showthread.php?p=6330827&highlight=fsck+-a#post6330827) 

I posted a reply but then realized that this one was done quite a while ago and I am not sure if I will get a reply. 

I was wondering if anyone could tell me how to identify my SD card from these hardware profiles: 

```

$ sudo fdisk -l 

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 9054 72678060 7 HPFS/NTFS
/dev/sda3 9055 9315 2096482+ f W95 Ext'd (LBA)
/dev/sda4 9316 9729 3325455 db CP/M / CTOS / ...
/dev/sda5 9055 9315 2096451 dd Unknown

```

I don't know which one belongs to the media card. No other external devices are plugged in. Want to run a sudo fsck -a on the media card. 

The 'mount' and 'dmesg | tail -20' commands in the other forum didn't seem to give me anything. 

I would really appreciate any help or advice. When I insert the SD into my blackberry it says "The media card that you have entered contains errors, please run a disk checking utility from a computer". 

Many, many, thanks in advance.
 
Regards,
Max

---

### Post by neu2buntu on 2009-04-13
run the sudo fdisk -l again without the sd card inserted then eliminate .. SEE NEXT POST INSTEAD

---

### Post by neu2buntu on 2009-04-13
actually scrub that last post..... your card is not showing because it would be /dev/sdb......  perhaps try booting ubuntu with the sd card inserted and run the fdisk command again

---

### Post by Max Avion on 2009-04-18
I will try that thanks.

---

