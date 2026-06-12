---
title: "iomega zip100 parallel port drive"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by jnorthr on 2007-08-02
Just thought i'd bring this to the top of the heap again with a bug port on [https://bugs.launchpad.net/ubuntu/+bug/110819](https://bugs.launchpad.net/ubuntu/+bug/110819) - have asked tim waugh to take a look at this as we believe he is more familar with ppa handling and its position in the stack of code layers supporting iomega zip drives.

---

### Post by Bert Mariën on 2007-10-20
Regarding the Iomega Zip Plus parallel drive, I got it working like this:

Made a mount point 

    /media/zip

Edited 
    /etc/modules
Added  
    imm 

Ran
    $ modprobe imm

Now its the trick to find where to find your disk.

Browse 
    /dev/.udev/names

You will find a directory there, most probably named
    disk\x2fby-label\x2fIOMEGA

When you open that directory, you'll find a file that tells you where to mount your zip drive. In my case the file was 
    \x2fblock\x2fsdb\x2fsdb4
so my zip drive was at 
    sdb4

Edited 
    /etc/fstab
Added 
    /dev/sdb4 /media/zip vfat user,rw,umask=0000,codepage=850 0 0
(codepage 850 is for Belgium)

Rebooted.
Everything worked.

---

### Post by ja06360 on 2007-11-24
Hi

I am having trouble with a Zip parallel port drive.

I have edited the /etc/modules file and added 'imm'

I have run modprobe imm

However I cannot find a directory in the /dev folder with the details of the zip drive (I know the drive is working as I can access this from Windows when I boot into this).

Any ideas?

Cheers
Jason

---

