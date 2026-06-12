---
title: "new motherboard bios."
date: 2008-07-12
forum: Hardware
---

### Post by matt$2 on 2008-07-12
hello gurus and everyone.


My dilemma is similar to one I found in a recent archive called something like  bios/grub-install, in fact identical.  Background events to my situation are;

my motherboard died.  Computer and cpu are 6 years old.
Tried getting a replacement model motherboard.  Ended up buying a new motherboard for 1/4 the price, plus a new cpu and a pci card to take a second IDE cable.  It has standard one IDE plug and four sata.  The motherboard is Asus P5N-MX for what it's worth.

The computer works as long as you don't boot up into any operating systems.

I bring up ubuntu on live CD, chroot to the installed ubuntu system.  The intention is to install new ubuntu's grub bootloader into the mbr of the first hard drive.   (There are three hard drives)  This BIOS is weird.  It will only list the IDE hard devices attached to its own connection, the others it does list, but under a raid device category.  Now everything falls apart.

CD live ubuntu sees all hard drives ok; one as /dev/hd0, the other two as /dev/sdcd & scdd.  Sure enough, one as a hard drive, the other two as raid types with sc notation.  mb scsi types combined with raid,  don't know don't care.  They are created and identified differently to how the old motherboard did everything.

Attempt
grub-install /dev/hd0    so as to fix everything and make systems bootable --- FAIL.
error  something like "bios does not have any corresponding BIOS drive", which I haven't seen before.  Grub insists on teaming up with the bios .
This looks like what happened to the poster of above mentioned and came with the following responses.


Yeah, I wish I could figure that one out.

Quote:
P.S. Obviously (hd0,7) is correct - and much easier because I don't have to worry about smilies.
Those smilies bug me to no end!

Anyway, glad it's working now. Enjoy. And mark as 'Solved' (>thread tools).
__________________
Food for thought: "Since the human genome is 3 billion base pairs long, 3 gigabytes of computer data storage space are needed to store the entire genome."

The chimpanzee genome is 95% identical to the human genome.
logos34 is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
logos34
View Public Profile
Send a private message to logos34
Send email to logos34
Find More Posts by logos34
Add logos34 to Your Contacts
Old January 16th, 2008 	  #7
adrian15
Way Too Much Ubuntu
 
Join Date: Jan 2006
Location: Iberian Peninsula
Posts: 286
Thanks: 0
Thanked 15 Times in 15 Posts
	
Re: grub-install/bios drive
Quote:
Originally Posted by vdhagen View Post
There remains just the curiosity why "grub-install /dev/sdd" didn't work and what "/dev/sdd does not have any corresponding BIOS drive" means.

It means that /boot/grub/device.map has not a line like:

(hd3) /dev/sdd

You can substitue (hd3) with whatever you want to.

You can also override device.map settings with the device command.

device (hd3) /dev/sdd

I'd like to be able to test it but the computer is in the computer shop where I bought it because of a separate hardware stuffup.  It's Saturday afternoon and I can't see getting it back before late Monday or later.

Can anyone confirm the solution to this boot breaking scenario is to adjust the device.map file so I can refrain from telling the vendors they've sold me a motherboard that clean bowls linux.

in anticipation

---

### Post by logos34 on 2008-07-12
Run this in a terminal on the live cd desktop and post the output:

[B]sudo fdisk -l

sudo lshw -C disk[/B]
> 
grub-install /dev/hd0    so as to fix everything and make systems bootable --- FAIL.You're mixing grub and linux drive designations.  If your chrooted into it, use 

sudo grub-install /dev/sdx 

OR 

sudo grub-install hd0

if you want to reinstall grub to the mbr

---

### Post by matt$2 on 2008-07-12
That looks good.  well done.  As my intro said, my computer is in the shop until tomorrow.  Now I want to go and get it back to execute this solution.  I'm using my son's computer in Windows!

The point is that the style I used worked perfectly well on the old motherboard.  I learned how to execute grub-install from the std help pages.  The (hdx,x) form I know by employing it in the grub menu.lst file.  Until now it just worked.
A change is as good as a holiday.
Will post when I can.

---

### Post by matt$2 on 2008-07-14
As good as it looked it was nonsense, though it shouldn't be and that's the whole point. Observe.

> ubuntu@ubuntu:~$ sudo mkdir /mnt/fedora
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/fedora
ubuntu@ubuntu:~$ sudo chroot /mnt/fedora /bin/bash
bash-3.2# grub-install hd0
Could not find device for /dev/sdb3
Could not find device for /dev/sdb3
Could not find device for /dev/sdb3
/dev/sdb3: Not found or not a block device. 

Let me make it clear.  GRUB IS STUFFED.

Who has reduced grub to a second rate meaningless piece of you know what.

For the last few years I have done exactly what the last person posted as suggestions.

Take note.  IT DOESN'T WORK ANY MORE.!!!!!


This is a grub problem.  Now at the moment I'm in a live Ubuntu cd (latest) working in a crummy coarse screen resolution courtesy of vesa.

I should be able to chroot into any of my many systems and do exactly what I've been doing for years.  

I have a fedora.  It used to boot perfectly allright.  Fedora is always fragile when it comes to booting up.  On this fancy new motherboard, I put the same hard drive in place as first hard drive, adjust the map file in /boot/grub so that first hard drive is hd0, not the second like it was,

adjust the other hard drive accordingly which carries the swap partition, and bingo.  Fedora fails at boot because it loses track of the root file system and /proc and /sys when it attempts to switch to the partition.  Nothing has changed.  This is not a grub draw back but it is in as much as I can not re-install grub from fedora or from any system into the mbr.

When I chroot into any system,  grub has decided in its wisdom that it MUST draw from the non-existant device objects in /dev/ of the system into which I've done chroot!!!!!!  Ofcourse there are non there, the system is not booted up and active.  It doesn't bother to take the hard drive device config from in this case the parent live cd.  Nor can I install a grub from the live cd because grub moans there is no boot device.  It's a live cd.!!!!@!

Any helpers to crack this catch 22.  I cannot get into any of my systems because of grubby grub.

---

### Post by bigken on 2008-07-14
have you disabled the raid in your bios it should be set to something like sata/ide

---

### Post by matt$2 on 2008-07-14
Well bigKen I can try, but I don't expect it will help.  Note all the things grub is not doing.  Whatever the setting in the bios, grub is looking for nonexistant device objects in the chroot system.  It was in fact doing this only just before the old motherboard died.  And If I do that, I'll have nowhere to go for the other 2 ide drives that I will soon get to re-add to my system because they get treated as raid drives.!!  !!!!!

Sure enough,  I can't find any setting in the bios to disable raid.  It shouldn't matter because the one drive is treated as an ide and the raid potential of the bios is inactive.

---

### Post by matt$2 on 2008-07-14
Oh and this. Now this time I'm using just one hard drive because the computer has an outstanding hardware issue that is stopping me from connecting the other two drives. That is another unrelated matter.

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdad699a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4021        9706    45672795    f  W95 Ext'd (LBA)
/dev/sda2   *        2567        4016    11642368+  83  Linux
/dev/sda3               1        2527    20290095   83  Linux
/dev/sda5            4021        5539    12194248+   b  W95 FAT32
/dev/sda6            5540        7137    12835901    7  HPFS/NTFS
/dev/sda7            7138        8800    13350928+  83  Linux
/dev/sda8            8801        9706     7277413+  83  Linux

Partition table entries are not in disk order


and 

> 
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD800BB-00FJ
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sda
       version: 13.0
       serial: WD-WMAJ91767537
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=dad699a4
  *-cdrom
       description: DVD writer
       product: DVD RW DRU-710A
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: BY02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted


If I had my way it would be three times as long.

---

### Post by matt$2 on 2008-07-14
Most curious.  I told you fedora was / is fragile.  Ubuntu has had a win.  I've piggybacked onto fedora's menu.lst and booted into Ubuntu Hardy on what is currently the first hard drive. It's only because I had a viable grub on 2 of my 3 hard drives, so just scraped in. Poor fedora, muffed it again.  They both had the same treatment and fedora got lost, again.  That can wait until later.  As nice as this is, the same query is still valid.  chroot into fedora from here and the same nonsense.

Grub is coming very close to being irrelevant to a quality setup.  It's developed another major fault I haven't even mentioned.

---

