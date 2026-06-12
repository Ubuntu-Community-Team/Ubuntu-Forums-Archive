---
title: "Problem with Grub(Windows-Linux conflict)"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by jl2035 on 2009-03-22
Hey!

I have a very stupid problem:

I had two OS' on my HP Compaq 6715s - Ubuntu 8.10 and Win XP. I formatted and reinstalled Win XP partition and since than I cannot boot Ubuntu anymore - there is no sign of it! Thanks to google I figured out that I have to repair 'Grub' - Link: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")
So I inserted Ubuntu 8.10 cd and selected "Try Ubuntu without any change to your computer". Than I couldn't find /boot/grub/menu.lst file, because /grub folder doesn't exist. When I opened the terminal I wrote "sudo grub", than "root (hd0,0)". But when I type "setup (hd0)", it says "error 17: cannot mount..."(something like that). 

(By the way: At least I can access my old Linux partition from here.)

Anyway I really hope I won't have to reinstall Linux. Is there any way to boot it again??? Because if there is, I'm sure that it's much more possible to repair grub loader from there.

---

### Post by hexanol on 2009-03-22
Could you post the output of "sudo fdisk -l" ?

You are in the good direction.

---

### Post by jl2035 on 2009-03-23
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e1a1e19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20481090    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2551        2688     1108485    5  Extended
/dev/sda3            2689        5824    25189920   83  Linux
/dev/sda4            5825       19453   109474942+   7  HPFS/NTFS
/dev/sda5            2551        2688     1108453+  82  Linux swap / Solaris

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders
Units = cylinders of 342 * 512 = 175104 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              24       11534     1968128    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by ubu-for on 2009-03-23
I have a similar problem and I knew already if I reinstall Windows, Grub won't load anymore. So after Windows did the job, I deleted it again by installing a second Ubuntu (Alpha 5). But now Grub takes always the menu.lst from my second Ubuntu (Alpha 5) on sdb1 and I had to copy the menu of my first Ubuntu (Alpha 6) to the menu.lst of my second.

How can I get Grub to load again my menu.lst from my first Ubuntu (Alpha 6) on sdc1.

```
Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000818a2

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000001

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217       30401   234428512+   5  Erweiterte
/dev/sdb5            1217        2189     7815591   82  Linux Swap / Solaris
/dev/sdb6            2190       30401   226612858+  83  Linux

Platte /dev/sdc: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000ccb

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1   *           1        2432    19535008+  83  Linux
/dev/sdc2            2433       60801   468848992+   5  Erweiterte
/dev/sdc5            2433        3648     9767488+  82  Linux Swap / Solaris
/dev/sdc6            3649       60801   459081441   83  Linux
```

Can I simply unmark the "boot" option for sdb1 with Gnome GParted?

And should I do the same for sda1, because it's not a hard disk with an OS?

---

### Post by ubu-for on 2009-03-23
> **jl2035 said:**
> Thanks to google I figured out that I have to repair 'Grub' - Link: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")
The HOWTO solved my problem for my hard disk (hd2) on sdc!

Thanks!

> To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd2,0)
- setup (hd2)
- quit

But I still get the message "Booting from (hd0,0)" and Ubuntu (Alpha 6) on my hard disk sdc (hd2,0) starts.

Everything is now fine but how can I get the message "Booting from (hd2,0)" where the OS really is?

---

### Post by jl2035 on 2009-03-23
So I have to make another linux partition and install Linux again...?
Please tell me there's another solution... :(

---

### Post by ubu-for on 2009-03-23
> **jl2035 said:**
> Please tell me there's another solution...
You've already found the HOWTO!

1. Find out which is actually your Root partition. It looks like yours is "sda3".

2. Look into your "device.map" at "/boot/grub" and you will find the correct hard disk identifier for Grub.

Here is my "device.map":

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

3. Follow the HOWTO with YOUR hard disk identifier.
[COLOR="Red"][B]
AT YOUR OWN RISK!

BACK UP YOUR DATA FIRST![/B][/COLOR]

If your Root partition is ACTUALLY "sda3" and your "device.map" is like mine, the "root" identifier for Grub is (hd0,2) and the "setup" identifier for Grub is (hd0).

---

### Post by jl2035 on 2009-03-23
> **ubu-for said:**
> You've already found the HOWTO!
...
2. Look into your "device.map" at "/boot/grub" and you will find the correct hard disk identifier for Grub.
...


If I boot Linux with a CD(which is the only way), I do not see the /grub folder. There is only /boot which has no subfolders just a few text files.

---

### Post by ubu-for on 2009-03-23
This is probably the "boot" folder from the Live CD, created at Live CD start up.

Start Nautilus, the file manager, and mount your hard disk. I hope your Ubuntu version can do that. If not, try the following HOWTO.

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Manually_Mount_and_Unmount_a_device](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Manually_Mount_and_Unmount_a_device)

---

### Post by jl2035 on 2009-03-23
Now I get it! I was a fool! :) I have to look for /boot/grub folder on the sda3 partition. I'll try right now..!

---

### Post by ubu-for on 2009-03-23
BTW You could also use the following drivers to read and write ext2/ext3 Linux partitions from Windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jl2035 on 2009-03-23
Amazing!!! I solved the problem. You were right 'ubu-for', root identifier for grub was (hd0,2). That's why it couldn't mount partition. Thanks for help!!!!!! :D  You're a genius!! :D

---

### Post by ubu-for on 2009-03-23
> **jl2035 said:**
> Amazing!!! I solved the problem. You were right 'ubu-for', root identifier for grub was (hd0,2). That's why it couldn't mount partition. Thanks for help!!!!!! :D  You're a genius!! :D
You're welcome!

Best regards!

---

