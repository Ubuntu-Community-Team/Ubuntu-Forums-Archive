---
title: "Backing up the MBR"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-07-19
2+ years ago, I installed Ubuntu 7.04 in /dev/sdg5, on the 4th hard disk drive.

Booting is controlled by Windows' NTLDR. I placed a copy of the MBR from /dev/sdg5 in the Windows C drive as grubboot.lnx.

The command used to create grubboot.lnx was:

```
sudo dd if=/dev/sdg5 of=/media/MicronM/grubboot.lnx bs=512 count=1
```

I included the following in C:\boot.ini

```
C:\grubboot.lnx="Ubuntu Linux"
```

I then modified menu.lst as follows:

```
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
rootnoverify (hd0,0)
makeactive
chainloader +1
```

However, after some point, each time I booted to Ubuntu, I would get a warning that the backup copy of the MBR did not match the real thing.

Yesterday, I found the following in [Backup & Restore]("http://members.iinet.net.au/~herman546/p13.html"):

> Warning:
Some web pages recommend that you should make a backup copy of the entire 512 bytes of your MBR, including the partition table and 55 aa signature.

That may be useful for some purposes, but be sure you destroy that copy of your MBR if you decide to re-partition your disk later. If you accidentally restore your MBR backup with an out of date partition table, it might not match the filesystems you have currently on your hard disk. It may cause some of your partitions to be unreadable.  
You will need to use TestDisk to write yourself a new partition table - [TestDisk Page]("http://members.iinet.net.au/%7Eherman546/p21.html").

Most people only need a backup copy of the bootloader code area, including the MBR's 'disk signature'. For that we only need the first 466 bytes of the MBR, so it will not include the partition table. That is much safer. That is what I do, and what is shown here. 

Does that mean I should use bs=446, instead of bs=512, in the dd to copy the MBR when I install 9.04?

---

