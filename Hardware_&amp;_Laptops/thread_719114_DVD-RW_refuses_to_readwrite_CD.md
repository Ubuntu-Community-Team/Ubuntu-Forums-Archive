---
title: "DVD-RW refuses to read/write CD"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by Tabenx on 2008-03-08
Good Evening,
Currently, my DVD-RW drive cannot read or write CD's. This started around last night and between now and then here is what i've tried:
[LIST=1]
[*]Reinstalled Ubuntu
[*]Tried Different CDs
[*]Inserted the same CDs in a different computer
[*]Checked my BIOS settings
[*]Contacted EMachine support(refused to help due to OS change)
[*]Begged, cursed, prayed, etc
[/LIST]
The strange thing is, it can still read and write DVD's with perfection. Please help!

---

### Post by BooBooNTZU on 2008-03-08
I think most of those problems come from security restrictions . Things like , read-only partitions , user account restrictions. 
In the case of DVD+RW or DVD-RW , i think you have to use the command line tools to blank/format the media completely and only after that , use a dvd burner program.
This is what i would try:

1. Edit your bootloader configuration to make sure none of the partitions use the  RO  (read-only) option
2. Enable the root account or try to remove all the user restrictions.
3. Add your user account to the ADMIN group or edit the user permissions.
4. Maybe boot into single-user mode  or recovery mode by pressing ESC when the bootloader starts.
5. When you reinstall Ubuntu try to partion it manualy and create a single partition formated as JFS. I had plenty of problems too when i used EXT3 .

Or you can try the following command in a terminal assuming that your dvd drive is allready detected:

sudo su 
then type your password , then type
dvd+rw-format -force=full /dev/dvd

It's gonna take a while to format the disk but , after that you can use any dvd burning program to record your cd / dvd.
It should work but your partitions are probably mounted as read-only and there are probably too many user account restrictions in the configuration.

To edit the bootloader and remove the RO option you can type :

sudo gedit /boot/grub/menu.lst     ---- for graphical editing
sudo nano /boot/grub/menu.lst     ---- without the graphical interface

You can allways press ESC before grub loads and edit the boot options to remove the ' ro ' read-only options
In the end your bootloader configuration should look somewhat similar to this , without any options after the root section :

title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=/dev/sda1
initrd		/boot/initrd.img-2.6.24-11-generic
quiet

In my case the hard drive is detected as scsi so it's   "root=/dev/sda" .... maybe yours is   "root=/dev/hda"   if the hard drive is detected as ide-generic. Make sure you remove all the options after the:    root=/dev/hda
Use can also use lspci command and lsmod command to see what kind of modules/drivers are loaded for what components. Maybe even use modprobe command to load other modules if things don't get detected properly.

Depending on your configuration and the number of partitions you have on your hard drive , the name of your boot partition could be different. You can allways try one of the following:

root=/dev/hda
root=/dev/hda1
root=/dev/sda1
root=/dev/sda

If you installed your boot partition on a memory card :

root=/dev/mmcblk0
root=/dev/mmcblk1
root=/dev/mmcblk0p1
root=/dev/mmcblk1p1

If the problem is only about cd's , then you might need to try :

1. Other recording software and other media.
2. Use different modules / drivers  or update the firmware for the dvd drive

---

