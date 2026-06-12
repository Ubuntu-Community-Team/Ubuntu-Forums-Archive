---
title: "Uninstalling Ubuntu 9.04 on an ASUS 900HA"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Epidemic_HardyBoy on 2009-05-27
Hello, I am asking if anyone here can tell me how to "Uninstall" my Ubuntu. I am dual-booting with windows XP on my eeepc from ASUS.

Specs:
Manufacturer  |	Asus
Model name    |	Eee PC 900HA
CPU type      |	Intel Atom (Diamondville)
CPU speed     |	1600 Mhz
Graphics      |	Intel GMA 950
OS            |	Windows XP Home
Display       | Size 8.9" 1024 X 600
RAM           |	1024 MB
Hard Disk     |	160 GB
Keyboard      |	YES
Mouse Pointer |	YES

I am uninstalling Ubuntu because of two reasons.

1) The GRUB bootloader is a pain since I have to pick XP most of the time
2) I virtually NEVER use ubuntu.

Can anyone please help me?

---

### Post by orange-wedge on 2009-05-27
First of all you can make Windows XP your default choice on grub by modifying /boot/grub/menu.list

To uninstall you will need to re-write the MBR on your hard disk.  So first you will need to create a Windows recovery flash drive.

[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

Then you will need to delete the linux parititions.  You could boot from ubuntu on your flash drive and use gparted to delete the partitions.  Then boot into Windows and format the extra drive you will see as NTFS.

---

### Post by Epidemic_HardyBoy on 2009-05-27
Is there a way I can get the Recovery Flash Drive?

---

### Post by Epidemic_HardyBoy on 2009-05-28
Bump.

Still looking for help with this

Do I partition away the ubuntu? If so, I would need to re-add the MBR, but the 900ha has no disk drive, how can I do this?

---

### Post by orange-wedge on 2009-05-28
Looks like there are a lot of Windows XP boot disk options on this site:
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Then you will need to find a copy of fdisk to re-write your MBR.

---

### Post by Epidemic_HardyBoy on 2009-05-29
I see, is there a way I can get any one of these on a flash drive?

Can I use the makeboot on a flash drive to make it compatible with a USB 2.0?

---

