---
title: "video problems with jaunty install"
date: 2009-07-08
forum: Hardware
---

### Post by Geoffzx6r on 2009-07-08
I just formatted my laptop and reinstalled vista. before I formatted I was dual booting vista and intrepid ibex. 

the laptop is a toshiba a215 that uses an ati x1200 video card. I've tried the 9.04 desktop iso off a flash drive using unetbootin. It boots and shows the ubuntu logo and then it goes into text mode. Is there a way to get this to work or do I need to use the alternate install iso? 

With the alternate install iso will I be able to resize the windows partition and create a new partition for the linux install?

Any help would be appreciated. Thanks in advance 

ps, oh I figure I can probably fix the video problem after the install by using the video drivers I used in the past for intrepid.

---

### Post by shatterblast on 2009-07-09
I think you can create a USB boot image through an Ubuntu LiveCD.  The item is called USB Startup Disk Creator.  It can be found under:

System -> Administration -> USB Startup Disk Creator

I think it requires the manual configuration of a few items.  As far as video drivers, I also suggest running "envyng-qt" from Synaptic.

---

### Post by Geoffzx6r on 2009-07-12
I already have a working iso, my problem is X isn't starting up.

---

### Post by shatterblast on 2009-07-13
If your computer BIOS has the option, you could try enabling something to the effect of USB devices booting first before CD-ROM drives, hard drives, or floppy drives.  A USB external might read as a USB-HDD device.

Otherwise, you will need to add the option of searching for a bootable partition within Vista's bootloader.  Also, it is possible to replace the Windows bootloader with something open source.  It would be good to use something like Clonezilla to back up your system before making these attempts.

Editting the Windows bootloader options will probably be safest for the integrity of your currently installed operating system.  Producing a mistake with an open source bootloader like GRUB can potentially damage your Windows install so that it will both refuse to boot and lose your data.

---

### Post by Geoffzx6r on 2009-07-13
I have no problem booting off the flash drive. I'm having issues with X not starting up

---

### Post by shatterblast on 2009-07-13
Are you familiar with a bootloader?  And does your system even try loading Linux?

---

