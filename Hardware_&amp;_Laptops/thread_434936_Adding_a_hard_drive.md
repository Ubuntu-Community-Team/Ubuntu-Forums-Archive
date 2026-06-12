---
title: "Adding a hard drive"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by xero 1ne on 2007-05-06
Hello, I am in a prediciment.

I am using an 80Gb sata hdd for my Ubuntu 7.04 install, and a 10Gb ide hdd for my swap(big, i know)

Grub for some reason is on the 10Gb drive, and I'm running out of space on my 80Gb, I want to add a new ide hard drive for me to slap my musik and iso's onto.

But when i plug in the hard drive as either a slave to the 10Gb, or even on its' own cable, Grub gives me "Error 5" when trying to boot.

I really need this, because I'm running out of space fast, If anyone can help that would be great!

(plus I don't want to waste all my dvd's)

---

### Post by Herman on 2007-05-07
Hello xero 1ne,
First you should make sure you have the new hard drive plugged in and jumpered correctly.
If you are using the IDE cables with black plugs, you should set the jumper for the master disk in the master position and jumper the slave disk in slave position, check for stickers or labels on your hard disk for instructions.
If you have cable-select IDE cables, (those have a blue plug that goes to the motherboard socket, a black plug to the master disk and a grey plug for the slave), then you should set both disks jumpers in the cable select position.

Then go into your BIOS and look check your [hard disk boot priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") you may be able to set your 80.0 hard disk to boot first in there if you have a CMOS that is programmable in that way. (I don't expect your BIOS to be the same as mine, but you might be able to do something similar).
You may need to edit your /boot/grub/menu.lst if that makes your hard disk numbers change.

Boot up your computer, and when you get to your grub menu, press 'c' for [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). 
Use the geometry command and tab completion as explained in the link I just gave you to find out which disk is which according to the way grub sees them.

Still in grub's command line interface, you should be able to re-install grub to your 80.0 GB drive like it should have done in the first place.

[                                                                         How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI")
Boot Ubuntu from Grub's Command Line Interface using the direct kernel boot method.
Keep notes of the detail you need to do that, because you might want to edit your menu.lst with those details later.

That should help you I hope,
Regards, Herman :)

---

### Post by Herman on 2007-05-07
Actually, there's an easier way:

First you should make sure you have the new hard drive plugged in and jumpered correctly.
If you are using the IDE cables with black plugs, you should set the jumper for the master disk in the master position and jumper the slave disk in slave position, check for stickers or labels on your hard disk for instructions.
If you have cable-select IDE cables, (those have a blue plug that goes to the motherboard socket, a black plug to the master disk and a grey plug for the slave), then you should set both disks jumpers in the cable select position.

Download a copy of [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and burn it to a CD or make a floppy or SuperGrub usbdisk, whichever you prefer.

Then go into your BIOS and look check your [hard disk boot priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") you may be able to set your 80.0 hard disk to boot first in there if you have a CMOS that is programmable in that way. (I don't expect your BIOS to be the same as mine, but you might be able to do something similar).
You may need to edit your /boot/grub/menu.lst later on if that makes your hard disk numbers change.

Boot [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and use it to re-install Grub to your 80.0 GB hard disk. 'English SGD menu'-->'Gnu/Linux'-->'Fix Boot of Gnu/Linux'-->'Fix Boot of Gnu/Linux (Grub). [COLOR=#000000][FONT=serif][FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]P[/FONT]ress your 'Esc' key. That will bring you back to the a menu. Then press your 'Return' (Enter) key to get back to 'English Super Grub Disk. 
Then go '[/FONT][/COLOR]'Gnu/Linux'-->' Boot Gnu/Linux Directly'

That way might be a bit quicker and easier, if you do need to edit your /boot/grub/menu.lst and you need help with it, post your output from 'sudo fdisk -lu' and someone should be able to help you then. ```
sudo fdisk -lu
```
Regards, Herman :)

---

