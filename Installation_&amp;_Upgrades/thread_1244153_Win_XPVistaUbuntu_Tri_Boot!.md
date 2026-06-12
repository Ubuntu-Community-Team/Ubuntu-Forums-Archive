---
title: "Win XP/Vista/Ubuntu Tri Boot!"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by madbunny on 2009-08-19
Hi all,

I just recently became interested in Linux after having a play on some machines at work. I decided to install Ubuntu on my PC but been having an issue with the boot side of things. This will be a lengthy post so as to give a background on what I've done so hopefully somebody wiser than me can pinpoint my problem!

I have 2 HDD's in my PC. In Bios, HDD1 is my 500GB HDD with Windows XP installed. It has 2 partitions, the XP OS and approx 400GB for Downloads etcc.

HDD2 in Bios is an 80GB which has Vista and Ubuntu Installed.

Originally I only had XP installed on HDD1 then I had added HDD2 and installed Vista. I was able to dual boot using the Vista Bootloader.

Then I shrunk the Vista Partition and installed Ubuntu.

When I booted I got the Grub Bootloader and was able to boot into all three OS's. Sweet!

What I was after though, was to have the Vista Bootloader handle everything so I installed EasyBCD on my Vista machine and followed an APC magazine article on how to add the Grub bootloader Menu to the Vista Bootloader.

Everything went wrong from here. Now when I boot i get the Vista Bootloader with three options:

1. Win XP
2. Vista
3. ubuntu

However, If I choose Ubuntu i get the Grub bootloader menu but when I choose to boot Ubuntu I get Grub Error 17.

I'll paste my Fdisk results and menu.lst file in case this can shed some light. Interested to see your comments as I've had countless Linux guru's at work stumped.

Thanks Guys!


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x090e090d

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       57473   410452717+   7  HPFS/NTFS
/dev/sda3           57474       60801    26732160    5  Extended
/dev/sda5           57474       60801    26732128+  bc  Unknown

 Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cb60cb5
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7562    60740156    7  HPFS/NTFS
/dev/sdb2            7563        9729    17406427+   5  Extended
/dev/sdb5            7563        9632    16627243+  83  Linux
/dev/sdb6            9633        9729      779121   82  Linux swap / Solaris
 *******************************************************************
END FDISK
*******************************************************************
 Only things not commented out on the menu.lst file below
*******************************************************************
Menu.lst
*******************************************************************
 title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9bc703ca-c945-4f7c-949d-c28a6d72af3d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9bc703ca-c945-4f7c-949d-c28a6d72af3d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

 title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9bc703ca-c945-4f7c-949d-c28a6d72af3d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9bc703ca-c945-4f7c-949d-c28a6d72af3d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic
 
title        Ubuntu 9.04, memtest86+
uuid        9bc703ca-c945-4f7c-949d-c28a6d72af3d
kernel        /boot/memtest86+.bin
quiet

---

### Post by tommcd on 2009-08-19
If grub was booting all 3 operating systems without problems, then I would stick with that. You can always restore the Vista MBR if you decide to go back to Windows.
To restore grub to the MBR, see this:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
To restore the Vista MBR, see these:
[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)
[http://www.howtogeek.com/forum/topic/how-to-restore-vista-mbr-without-vista-disc](http://www.howtogeek.com/forum/topic/how-to-restore-vista-mbr-without-vista-disc)
[http://ubuntuforums.org/showthread.php?t=596507](http://ubuntuforums.org/showthread.php?t=596507)

And welcome to the Ubuntu forums!

---

### Post by madbunny on 2009-08-19
Thanks, Is it possible to make Grub load XP as default OS after a 5 second timeout?

---

### Post by tommcd on 2009-08-19
> **madbunny said:**
> Thanks, Is it possible to make Grub load XP as default OS after a 5 second timeout?
Yes it is. First, backup your grub menu.lst for safety:
```
sudo cp /boot/grub.menu.lst /boot/grub.menu.lst.bak
```
then edit the grub menu.lst and put the Windows XP entry *above* (not inside) the ###Debian Automagic kernels list####.
as described in the section:
**Changing the default (operating system booted by the timer)**
on this page:
[http://members.iinet.net.au/~herman546/p15.html#menu.lst](http://members.iinet.net.au/~herman546/p15.html#menu.lst)
To edit the grub menu, just run: **gksudo gedit /boot/grub/menu.lst** and cut and paste the entry for XP so that it is above the Debian Automagic Kernels list.

---

