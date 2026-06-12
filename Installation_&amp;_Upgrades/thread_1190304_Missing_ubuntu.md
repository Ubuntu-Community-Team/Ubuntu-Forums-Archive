---
title: "Missing ubuntu"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by m4tic on 2009-06-17
I use ubuntu and i installed windows today. The ubuntu boot loader is missing. Wat shoul i do? Sodu grub doesn't work but only grub works and after trying find /boot/grub/stage1 
root (hd0,0) then 
setup (hd0) no luck. 
Tel me what should i do, i hav two partitions 1 ntfs and one ext3

---

### Post by m4tic on 2009-06-17
Help me

---

### Post by merlinus on 2009-06-17
Enter this command in a terminal window:

```

sudo fdisk -l

```

It will show which partition is ubuntu.  Then you can reinstall grub.

---

### Post by m4tic on 2009-06-17
Thanks, let me try it out

---

### Post by m4tic on 2009-06-17
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfaa5faa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5965    47913831    7  HPFS/NTFS
/dev/sda2            5966        9726    30210232+   5  Extended
/dev/sda5            5966        6081      931738+  82  Linux swap / Solaris
/dev/sda6            6082        9726    29278431   83  Linux

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00058e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3816      976880    b  W95 FAT32
ubuntu@ubuntu:~$ 


Uhm wat should i do now?

---

### Post by m4tic on 2009-06-17
Hello

---

### Post by merlinus on 2009-06-17
First of all, patience furthers.  None of us is gettting paid to help!

Try this:
```

sudo grub
root (hd0,5)
setup (hd0)
quit

```

More info here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by m4tic on 2009-06-17
Wow, thanks it works! U knw.. i was about to format if it wernt for u. thank u man

---

### Post by merlinus on 2009-06-17
Glad it worked!  Happy ubuntuing...

---

### Post by raymondh on 2009-06-17
> **merlinus said:**
> Glad it worked!  Happy ubuntuing...

merlin ... why ho0,5 ?  I Could not see it ????

---

### Post by merlinus on 2009-06-17
linux on sda6...  look at result of sudo fdisk -l.

---

### Post by raymondh on 2009-06-17
> **merlinus said:**
> linux on sda6...  look at result of sudo fdisk -l.

arrggh, you're right ... I went brain dead on the linux numbering system.

"starts from 0, raymond ... from ZERO"

Thanks Merlin :)

---

### Post by m4tic on 2009-06-19
Thanks again,

---

