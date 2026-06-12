---
title: "Hard Drive Fail"
date: 2013-03-03
forum: Hardware
---

### Post by willy-be-frantic on 2013-03-03
I haven't been on here in quite some time.  Therein lies the problem.  A few years back I installed Ubuntu on 
top of Windows XP ( GRUB bootloader ) and never really used it much.  Went on the odd time.  
Updated a few times and eventually the OS hung while updating.  No matter.  Used XP and 
finally had problems booting Windows XP.  Took mini-tower ( older Dell ) to the shop and 
they said the hard drive cannot be read.  They replaced the hard drive, reloaded Windows XP 
and I'm up and running.  Of course all the data on the old drive is unavailable.  Back-ups 
you say ?  Heck of a theory, sadly not implemented.

When I installed Ubntu it re-partitioned the hard drive, made a space for all the Windows C: 
drive and did all the other things needed to make it all work.

Since the hard drive fail and the install of a new hard drive and Windows O/S I installed the original hard drive as a 
slave drive in the Dell.  If I boot the machine and quickly hit _F10_ I get the boot selector which 
doesn't show the slave drive as being a bootable drive.  If I boot the machine and quickly hit _delete_ 
I get the BIOS menu and the slave drive shows up there.

I then used a Linux boot disc ( gparted-live-0.14 ) to boot the machine. On first boot the 
graphic screen comes up and 'gparted' starts, looks for devices, finds /dev/sda and then 
hangs looking for\at /dev/sdb.  If I close 'gparted' and then restart it, it looks for 
devices and then hangs, without ever saying it found /dev/sda.

I then bring up a terminal screen.

#ls /dev/sda

returns

/dev/sda [ in bold and coloured letters ]


#ls /dev/sdb

returns

/dev/sdb [ in bold and coloured letters ]

I'm assuming that the live boot O/S can at least find both drives.

#fdisk /dev/sdb  *or* /dev/sdb1

returns

unable to open : permission denied

#cfdisk /dev/sdb

returns

Fatal Error


Whats the trick to looking at and coping Windows Partition files off the slave drive ?

I'm assuming the live boot disc would give me superuser permissions.  Do I need to 'chmod' 
on /dev/sdb ?  Do I need to unmount /dev/sdb to run cfdisk ?

I don't want to admit that the hard drive ( currently slaved ) is totally corrupted and all 
data is unrecoverable.  It may well be but I don't know how to say for sure.

Thanks in advance.  This was always a helpful place when I was here before.

---

### Post by tgalati4 on 2013-03-03
The general procedure:

Boot any linux live CD.  Have a working network cable plugged in.

Open a terminal.

sudo apt-get install testdisk

man testdisk

man photorec

Have plenty of USB flash drives or another external drive (like a large USB drive) to receive the data.

Testdisk will try to recover the directories and partitions if they are messed up.

Photorec will try to recover any individual files, but all in one massive directory.

---

### Post by tgalati4 on 2013-03-03
The general procedure:

Boot any linux live CD.  Have a working network cable plugged in.

Open a terminal.

sudo apt-get install testdisk

man testdisk

man photorec

Have plenty of USB flash drives or another external drive (like a large USB drive) to receive the data.

Testdisk will try to recover the directories and partitions if they are messed up.

Photorec will try to recover any individual files, but all in one massive directory.

(Trying desparately to increase my bean count with double posts.)

---

### Post by willy-be-frantic on 2013-03-03
Thanks tgalati4

Best of luck with the bean count.

I was not able to get a network \ internet connection with my wireless card on my machine.  I will plug in a cable and go hard wire.  I have a USB card reader with a 32 GB card that should be enough to hold the data.  I don't know if the live boot disc is seeing the card reader.  I'll boot with the card in the reader ( it should show up as /dev/sdc, I assume ).  The card currently has some files on it which would be under a general Windows format.  When I get data off the hard drive I can then worry about getting the file onto \ into the |Windows environment.

---

### Post by willy-be-frantic on 2013-03-03
Update - Wasn't able to get a network\ internet connection with the machine hard-wired to my router.  No matter.  Both *testdisk* and *photorec* were on the gparted-live bootdisc.  

#photorec /dev/sdb

returns

Unable to open file or device /dev/sdb

#dosfsck /dev/sdb

returns

dosfsck 3.0.13 30 Jun 2012 Fat32, LFN
open: Permission denied

How do I tell if the is still uncorrupted data on /dev/sdb ?  Can I list what partitions are on the hard drive ?  Can I look at the drive without looking at the partition table by somehow using "cfdisk -z".  Should I be trying to run a command on /dev/sdb1 *or* 2 *or* 1a or something ?

---

### Post by justincarter on 2013-03-04
I think first you should check whether hard drive has been crash or not. Change the setting of boot-loader and boot from external hard drive and some other options. If you still face problem then you should go to a laptop repair center.

---

### Post by willy-be-frantic on 2013-03-04
Thanks Justin

I am not trying to boot from the drive, just trying to recover some data from the drive.  I have taken the machine to a repair shop.  They did say the drive is unreadable.  Just hoping there was a way to get into it.  It does look, in some instances, that the drive is readable.  Looking for a command or the correct syntax or the correct settings that would allow me to get a look at it.

Thanks again.

---

### Post by willy-be-frantic on 2013-03-04
Thanks to all.

I searched around the forum and found a step-by-step listing by Mark Phelps where he said he had good luck with *RecoverMyFiles* software. It cost $70 but it worked.  Props to you Mark.  Made my day.  

As a side note, two different computer stores said the drive was trashed.  No recoverable data.

This thread could be marked closed / solved, but I don't see how to do that.

Thanks again.

---

