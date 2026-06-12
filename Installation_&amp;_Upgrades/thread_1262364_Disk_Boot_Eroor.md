---
title: "Disk Boot Eroor"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by Maci_01 on 2009-09-09
The classic failure to find disk boot error. When I start up my computer after a short delay my computer fails to find a suitable boot loader, giving the error boot disk error (or something similar).

So my computer is functioning, but only after I insert a bootable CD. Are there any suggestions as to how to fix the boot sector and/or the MBR? Pointing me to a similar thread would be great. 

Here's some additional info if you have time:

I woke up to find my computer wouldn't boot at all. It turns out it was the power supply, so I switched it with a spare I had. Then started it up again to find the error. I checked to make sure all the cables were fitted properly, they were. 

I inserted my Windows XP installation disk, but instead of booting to the disk I waited and it bypassed to the regular MS boot loader. I successfully logged into XP (yay). Keep in mind that I was triple booting: XP, Vista and Windows 7.

Everything worked but not quite as it should, still needed a CD to boot. So something was up with my boot sector, so I thought I could install good ol' Ubuntu and it would renew the boot sector, installing grub and all would be well. Well I installed Ubuntu but the disk boot failure message keeps coming up. I need a bootable CD to start up GRUB now, instead of the MS loader.

Any suggestions?

Thank you,
Joe

Edit: The exact message is &#8220;Hard disk boot failure, insert system disk and press enter&#8221;.

---

### Post by VMC on 2009-09-09
> **Maci_01 said:**
> ... It turns out it was the power supply, so I switched it with a spare I had. Then started it up again to find the error. I checked to make sure all the cables were fitted properly, they were. 

...Since you had some hardware failure, I wonder if you BIOS got messed up somehow. Were you booting off of grub or Windows boot manager? If grub, put Ubuntu boot disk back in, go to a terminal and output "sudo fdisk -l" for starters

---

### Post by Maci_01 on 2009-09-10
I have three hard disks, however, all operating systems are located on the first hard disk. Here is the output for that:


> Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a6e1a6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6674    53608873+   7  HPFS/NTFS
/dev/sda2            6675       13350    53616640    7  HPFS/NTFS
/dev/sda3           13350       13375      204800    7  HPFS/NTFS
/dev/sda4           13376       20023    53400060    5  Extended
/dev/sda5           13376       19658    50468166   83  Linux
/dev/sda6           19659       20023     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f28ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50602   406460533+   7  HPFS/NTFS
/dev/sdb2   *       50603       60801    81923467+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x40ee023f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      310101   156290400    f  W95 Ext'd (LBA)
/dev/sdc5               2      106368    53608936+   7  HPFS/NTFS





Thank you!

---

### Post by dandnsmith on 2009-09-10
Since you (OP) haven't quoted the exact boot failure message, I find diagnosis tricky, but the whole thing sounds like the first HDD may be slightly damaged.

Are you always starting to boot from the power-on, or do you ever try a reboot?

One PC HDD I had would refuse to boot at first, but, given time to warm up, would later - I used to boot with a blank/non-bootable floppy, wait (after the messages indicating failure) for a while, and then restart with ctrl-alt-del: it would then boot.

---

### Post by Maci_01 on 2009-09-10
EDIT: Problem solved. I booted into the motherboard BIOS, hitting DEL on startup. Reset to default settings, upon restart my default boot was recognized.

Although unused, here are some useful resources I discovered.
[ReInstall Grub from the Ubuntu Live CD]("http://ubuntuforums.org/showthread.php?t=224351")
[10 Things you can do when Windows XP won't boot]("http://faq.programmerworld.net/ms_windows/10-things-to-do-when-windows-xp-wont-boot.html")

Whenever trying to fix boot problems, proceed with absolute caution. As an inexperienced user you may find yourself reinstalling your operating system and/or potentially losing valued data.

---

