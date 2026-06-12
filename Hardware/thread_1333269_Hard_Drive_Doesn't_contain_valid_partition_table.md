---
title: "Hard Drive Doesn't contain valid partition table"
date: 2009-11-21
forum: Hardware
---

### Post by Tjcrazy on 2009-11-21
This shouldn't really be posted in the ubuntu forums, but I am using ubuntu to fix it, so I think I can get away with it :).

Basically while I was running Windows 7 I wanted to clone my 149GB Hard Drive to a 500GB partition on my 1TB HardDrive, with Ubuntu taking up the other 500GB.

I coulnd'nt clone using Windows tools because I always had an error of some sort. I then tried cloning using various Ubuntu tools on the Live CD - these didnt work either. I then tried ```
dd if= of=
``` command and it copied about 50% before an I/O error.


After the dd failed I tried booting Windows 7. The boot manager gave me 2 options. **Win 7 ultimate** and **win 7 ultimate (recovered)** win 7 ultimate never booted, because it was the new-er, half-cloned HD. The other windows loaded but was bugged, had to manually run explorer etc.

I then tried using Windows 7 Installation CD to repair my installation. Nothing worked. I ended up formatting the 1TB HD - thinking that it would work. Now I cannot load up the older Windows 7 installation! I went back into the recovery console and deleted the Windows 7 volume in diskpart - Which I don't think helped.

I load up my Ubuntu Live CD and look at gParted. I am shocked when it says both Hard Drives are 100% un-allocated. I then try sudo fdisk -l which returns:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c56bc

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

/dev/sdb = Old 149GB Hard Drive - should contain Windows 7
/dev/sda = New 1000GB Hard Drive - should be empty.

Now I am stuck - I wouldn't mind re-installing Windows 7, but NEED some of the stuff on the Hard Drive.

Maybe a dd would help, but could make things worse?!?!?

Thanks in advanced

---

