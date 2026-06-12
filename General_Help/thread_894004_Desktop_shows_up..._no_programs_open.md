---
title: "Desktop shows up... no programs open"
date: 2008-08-18
forum: General Help
---

### Post by carl19_68 on 2008-08-18
Hi y'all,

I recently had the bright idea to change the size of my swap partition, so I popped in GParted and chopped it in half.   After a failed boot up ( the desktop appeared, but I never could open any program), I changed the partition BACK to the orginal size.  Now, the same thing occurs,  login in and desktop shows. but the hard drive spins all night and all day.  

Is there some way to restore this thing back to how I had it without reinstalling ubuntu?

By the way, I am running Hardy Heron.

Thanks,

Carl

---

### Post by jualin on 2008-08-18
Please go to the terminal and type > sudo fdisk -l and post the results on the forums. This will show us the hard drive partitions.

---

### Post by carl19_68 on 2008-08-18
thanks for the quick response  fdisk-l yields:

Disk/dev/sda: 20.4 GB 20416757760 bytes
255 heads, 63 sectors/track,2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier : 0x000498cc

Device       boot    Start    End   Blocks     Id   System
/dev/sda1      *       1      2437  19575171   83   Linux
/dev/sda2            2438     2482    361462+   5   Extended
/dev/sda5            2438     2482    361431   82   Linux swap/
                                                    Solaris

---

### Post by jualin on 2008-08-18
I think that the problem is that you didn't put the SWAP size back correctly. I suggest booting a Live CD and then opening Gparted from there. Once in Gparted, delete the sda2 and sda5 partitions, create a new partition with the new free space (sda2+sda5) and make it a swap partition. Feel free to ask me if you don't understand something.

---

### Post by jualin on 2008-08-18
Before you do what i suggest, have you made another partition (sda2) for about 360 MB or was this the chopped part from your original SWAP partition?

---

### Post by carl19_68 on 2008-08-18
the 360 was the original size of the partition, I just had written the size down, tried it, and since it didn't work, I put it back.  Guess I "clicked" when I should have "mashed" or visa versa...

So should I follow your original recommendation of "delete the sda2 and sda5 partitions, create a new partition with the new free space (sda2+sda5) and make it a swap partition"?

And by the way, I haven't figured out how to thanks people on here other that saying it....

so Thanks! in advance.

---

### Post by jualin on 2008-08-18
Yes, follow my suggestion of creating a new partition with both sda2 and sda5 partitions. Good luck!

---

### Post by Hyper Tails on 2008-08-18
Try this
```
sudo dpkg --configure -a
```

enough said

---

### Post by carl19_68 on 2008-08-20
Well, I hate to say it;but, I tried both suggestions and neither worked.  After logging on , I cannot open any programs.  There is a disk shaped icon next to the pointer, much like an jourglass appears on windows.

Any other suggestions?

---

### Post by jualin on 2008-08-22
If nothing else works out, then you would need to reinstall your Ubuntu, since it could be faster that waiting for someone else to give you a different idea. Good luck!

---

