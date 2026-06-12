---
title: "Installing Ubuntu without cdrom, usb or second hard drive"
date: 2008-07-16
forum: Hardware
---

### Post by scrime on 2008-07-16
Hello all,

I'm trying to set up a computer with Ubuntu.  It is an old HP e-vectra e-pc C-10, PIII 700mhz Celeron ([HP Link]("http://h20000.www2.hp.com/bizsupport/TechSupport/SupportTaskIndex.jsp?lang=en&cc=us&taskId=110&prodTypeId=12454&prodSeriesId=32384")). I upgraded the RAM to 256mb PC133 and swapped the HDD for a 27gb Western Digital 7200rpm drive.  The problems with installing Linux are as follows: It doesn't have a CD-ROM, I considered getting a IDE laptop HDD because the CD-ROM connection is the same, although it doesn't have a power connector, this is because it uses a non-standard type of CD-ROM.  I can't/wont buy one.  So that ones out.  It doesn't boot from USB, although the option is in the BIOS, according to HP's website they never designed the BIOS hooks in order for this to work.  The primary IDE channel is designed to accommodate only 1 HDD.  I can install Win98 by formatting it FAT32 and copying the installation files onto the drive from another PC.  The problem I have with this is a machine with Win98 on it is little more than a doorstop.  I want to install Ubuntu.

I've been considering creating a small EXT3 partition on the drive on my PC, then using syslinux to make the HDD bootable and copying the Ubuntu installation files onto the small partition.  Will this work or has anyone done this before?  When grub installs will it sort out the bootsector/MBR correctly?  I would then want to remove the installation partition, and mount the space to another point.

I know this sounds like a waste of time, I'd really like to do this for my father who will use the machine to play videos over the projector for his video club.  I know this is the only way to breath new life into to the old machine.

Regards,
Mark.

---

### Post by logos34 on 2008-07-16
If you have internet access on win98, try downloading and installing ubuntu via [UNetbootin.]("http://lubi.sourceforge.net/unetbootin.html")

Or else try this method:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'CD Image Approach')

If none of the above works then come back to the ext3 idea you mentioned (but it will require some effort if it works at all)

---

