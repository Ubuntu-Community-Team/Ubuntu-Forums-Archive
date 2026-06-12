---
title: "Formatting challenge"
date: 2008-08-22
forum: Hardware
---

### Post by CTRLurself on 2008-08-22
I have a unique challenge for the Ubuntu community - I need to figure out a way to do one of two things:

A) format a HDD into CDFS format so i can dump an .ISO file to it as a bootable partition

or 

B) I need a way to put an .ISO file onto a partition by itself in a way that it will read that .ISO file as though it were on a disk, all outside of any OS environment.

Essentially I need to either make a .ISO file bootable on hard disk without emulation or I need to make a partition think it's a disk so an .ISO file will boot.

And I realize that if/when I get the hard drive into CDFS file structure I have to do a dump to actually get the .ISO onto the "read-only" CDFS format. Also, I currently have a Windows, an Ubuntu and an OSX environment on the computer, so if the solution is cross-platform, that's not a problem for me.

Thanks for any help you can offer, and if I figure it out I'll be sure to post instructions on here.

---

### Post by az on 2008-08-22
Can you give more details about the actual problem you are trying to solve?

I don't think your motherboard will be able to boot something in CDFS.  So A is out.

As for "B", is it a linux bootable iso?  In that case, just copy the files from the iso image to fat filesystem on the partition and change isolinux to syslinux.  You need to change isolinux.cfg to syslinux.cfg and run syslinux on the unmounted partition.  Then the partition is bootable.   You just need to get your motherboard to boot that partition.

---

### Post by CTRLurself on 2008-08-22
Firstly, CDFS is bootable on all modern motherboards, it's the format of a CD or DVD when you burn ISO's and other data to them.

Secondly, I'm personally doing this to ease my tri-boot situation, but I know of several other applications this could be used for.

My application is a bit more complicated to understand at first. I'm tri-booting Windows Vista Ultimate 32-bit, Ubuntu 8.04 64-bit, and OSX 10.5.2 all on an HP laptop.

When I turn on my computer if the OSX install disk is in the tray, it'll auto-boot OSX, if it's not then i get the GRUB menu for Vista or Ubuntu. I'm trying to find a way to eliminate this either-or scenario (and the need to keep the disk around at all times), and put the disc directly onto my HDD so i can choose any of the three from GRUB.

The caveat is, OSX on a PC requires a modified install disk in the drive to boot off of the disk even after the OS has been installed. The disk essentially just loads the HFS file structure and then points to the OSX partition to boot after the OS has been installed.

The applications for this are the real reason I'm trying to do this... it's an idea i've had for a while, it's why i got into Ubuntu - I thought it would help me learn enough to do this on my own, but i cannot. So i'm asking for help from the community

---

### Post by Loaded.len on 2008-08-22
if the ISO's are actually bootable images, then maybe what you want is to format your drive using fat32, install grub4dos, and use isolinux to read the ISO files and boot them as if they were mounted and running live.  I used to do that on my 2gb USB key.

---

### Post by CTRLurself on 2008-08-22
> **Loaded.len said:**
> if the ISO's are actually bootable images, then maybe what you want is to format your drive using fat32, install grub4dos, and use isolinux to read the ISO files and boot them as if they were mounted and running live.  I used to do that on my 2gb USB key.

well, there's one ISO file, and 2 normal OS's installed, but I'll take a look into it... My real goal would be that ideally after formatting all I'm really needing to do is dumping the ISO file to the partition, but anything could help.

Thanks.

---

### Post by Loaded.len on 2008-08-22
well, it's almost that easy when you've got it setup that way.. you still need to edit the grub menu.lst whenever you pop a new ISO in or change it.

---

### Post by CTRLurself on 2008-08-23
I may be wrong but:

From what I've read, grub4dos is a replacement for GRUB which I'm using now.

and I have yet to find a good simple explanation for using Isolinux anywhere. I understand the concept, but the best explanation for using it I've found it is here: [http://members.chello.at/bobby100/ILpart1.htm](http://members.chello.at/bobby100/ILpart1.htm) but they either assume I already know what I'm doing, or they assume that I'm using Linux.

I'm using an ISO file that I can't unpack because it's internal file structure is not in a recognizable format (i'm actually about to try unpacking it in OSX and converting it to a windows/ubuntu format and see if i can get the files out of it).

---

### Post by Loaded.len on 2008-08-23
This forum post helped me a lot when I was doing my USB thing.  

[http://www.911cd.net/forums//index.php?showtopic=18846](http://www.911cd.net/forums//index.php?showtopic=18846)

There's a LOT of useful boot type info on that site... but sometimes you need to stitch information together from a couple or more posts

---

### Post by CTRLurself on 2008-08-23
> **Loaded.len said:**
> This forum post helped me a lot when I was doing my USB thing.  

[http://www.911cd.net/forums//index.php?showtopic=18846](http://www.911cd.net/forums//index.php?showtopic=18846)

There's a LOT of useful boot type info on that site... but sometimes you need to stitch information together from a couple or more posts

i get stuck at the step where it tells you to install syslinux to the flashdrive... it doesn't say how to run the command (i'm not sure if i should be in linux or windows at this step) and i couldn't even command line it, so i have no idea.

---

### Post by livestockPimp on 2008-08-23
Would something like this help?
there are a few solutions here that may work.
[http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/](http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/)

---

### Post by CTRLurself on 2008-08-23
so here's what i'm going to do.

1) create a partition that is 8GB (the OSX disk size, plus a little extra) format as FAT

2) create a menu.txt and syslinux.cfg file there with the appropriate contents

3) SOMEHOW GET syslinux.exe to run and create a ldlinux.sys file here (this is the first problem i run into)

4) I need to extract the ISO file into the root directory of the partition, and find out what the boot files are (I'll check the insanelymac forum for this one). Edit the syslinux.cfg and menu.txt file to include this option.

5) figure out how to make it auto-boot this option

6) edit GRUB to include the option to boot off of this partition (which in turn actually boots off of another partition).

7) remember how i did everything and share it with the community... and then finalize my idea for it's broader application.

If somebody can help me with steps 3 through 5 that would be AWESOME... but for now I'm going to bed.

---

### Post by CTRLurself on 2008-08-23
> **livestockPimp said:**
> Would something like this help?
there are a few solutions here that may work.
[http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/](http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/)

that would appear to be perfect... i'll still need to figure out what the bootable file is for OSX, but I'll get back to you with the results.

Thanks a bunch

---

### Post by az on 2008-08-23
> **CTRLurself said:**
> 

3) SOMEHOW GET syslinux.exe to run and create a ldlinux.sys file here (this is the first problem i run into)

4) I need to extract the ISO file into the root directory of the partition, and find out what the boot files are (I'll check the insanelymac forum for this one). Edit the syslinux.cfg and menu.txt file to include this option.

[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)

sudo apt-get install syslinux

syslinux /dev/sda1 (assuming the device is sda1 - Use the correct device name!)

> **CTRLurself said:**
> 
5) figure out how to make it auto-boot this option

6) edit GRUB to include the option to boot off of this partition (which in turn actually boots off of another partition).

7) remember how i did everything and share it with the community... and then finalize my idea for it's broader application.

If somebody can help me with steps 3 through 5 that would be AWESOME... but for now I'm going to bed.

You can add to these pages, as appropriate:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by CTRLurself on 2008-08-23
> 1) create a cd sized partition (700 gb or slightly larger) or a dvd sized partition (4.5 gb or thereabouts).

2) format the partition iso9660 (in essence, creating a cd disk on the hard drive).

3) burn the iso to the new partition just as you would burn to cd, specifying cdrom=/dev/hdX,Y (the partition on the drive instead of the cd drive).

4) add an entry in your grub conf file to point the the new partition, something like:
title some_live_cd
root (hdX,Y) # where X,Y is the partition you just created)
chainloader +1


in step 2 it says to format the partition as iso9660. I understand why, I know what it is, but I don't know how to actually do it. Can i command line it? or do it with GParted (I don't have my laptop handy right now to check)? or do i need to use something else?

for step 3 i cannot find the full command line I need to burn a disk, just "use *cdrom=/dev/hdX,Y*" I did however find 

> 3. Make a temporary directory to mount the iso into: mkdir /mnt/iso.
4. Make a mount point for /dev/hda4: mkdir /mnt/hda4.
5. Mount the iso: mount -t iso9660 -o loop /path/to/image.iso /mnt/iso. Then mount hda4: mount /dev/hda4 /mnt/hda4.
6. Copy the mounted iso into hda4: cp -R /mnt/iso/* /mnt/hda4.
7. Unmount the iso: umount /mnt/iso.


which would accomplish the same thing in a more round-about way.

And step 4 would be easy if i can figure out steps 2 and 3... again, any help would be appreciated.

---

### Post by az on 2008-08-23
> **CTRLurself said:**
> in step 2 it says to format the partition as iso9660. I understand why, I know what it is, but I don't know how to actually do it. Can i command line it? or do it with GParted (I don't have my laptop handy right now to check)? or do i need to use something else?

for step 3 i cannot find the full command line I need to burn a disk, just "use *cdrom=/dev/hdX,Y*" I did however find 



which would accomplish the same thing in a more round-about way.

And step 4 would be easy if i can figure out steps 2 and 3... again, any help would be appreciated.

man wodim
man mksiofs

---

### Post by CTRLurself on 2008-08-23
> **az said:**
> man wodim
man mksiofs

please clarify, because that means nothing to me... like which one does what.

---

### Post by az on 2008-08-23
*man* is the command to see the manual to command-line programs.  The programs you are asking about are called wodim and mkisofs.  Typing

man wodim

will show you the manpage to Wodim.  

To see how to use the mkisofs (MaKe ISO FileSystem), type

man mkisofs

---

### Post by CTRLurself on 2008-08-24
first off I was able to sudo syslinux, it downloaded fine, but when i did the "syslinux /dev/sdb1" i got a 

> /dev/sdb1: Permission denied


i tried this on a flash drive (sdb1) in fat16, fat32 and ext3 format

next, i couldn't figure out anything using the mkisofs command other than it's not "man mkisofs" it's "mkisofs -help" but the help was little use for how to format the partition as iso9660. it gave modifiers, but no real instructions on it's basic usage (people always assume everybody knows the basics of all of ubuntu)

so i moved onto wodim which had MUCH better documentation

I tried "wodim -force -format dev=/dev/sdb1" which was me attempting to force format a flash drive to cdfs in wodim, but it gave me the error:

> wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.wodim: Permission denied. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.


so i tried "wodim -force-raw96r dev=/dev/sdb1" and it said

> wodim: No tracks specified. Need at least one.
Usage: wodim [options] track1...trackn


and it gives very bad instructions on how to specify a file but something i think will be important is:

>  -data  If  this  flag  is present, all subsequent tracks are written in CD-ROM mode 1 (Yellow Book) format. The data size is a  multiple of  2048  bytes.   The  file  with  track data should contain an ISO-9660 or Rock Ridge filesystem  image  (see  genisoimage  for more  details).

so i did "genisoimage -help" which was about as helpful as "mkisofs -help" in fact i'm fairly certain they are the same program (the help files looked identical)

the file is in .ISO format, but I'm not sure how to specify the file, so i think the command i need will be, "wodim -force -raw96r dev=dev/sdb1 -data /bin/kalyway.iso" where "dev/sdb1" is the target partition (temporarily a flash drive) /bin/kalyway.iso is the file's location. I'll be testing this shortly (I'm having drive permission errors right now that will be remedied be a quick re-install because I'm not patient enough to fix drive permissions for about 12 drives/partitions).

And if anybody would like to take a look at the "genisoimage -help" file and try to help me figure out how to burn a bootable ISO file to a hard drive partition/flash drive, it would be much appreciated.

---

### Post by Loaded.len on 2008-08-24
This works fine for me.  ```
sudo syslinux -s /dev/sdb1
```

NOTE: you don't NEED the "slow and stupid switch" (-s) But in my case I use this on a USB key so I don't always know how other BIOSes will react.

---

### Post by CTRLurself on 2008-08-24
Attempting a different method:

1 - format flash drive as fat32 (it's sdb1) I used Gparted
     a - *sudo apt-get install gparted*
     b - *sudo gparted*
2 - *sudo apt-get install syslinux mtools*
3 - *sudo syslinux /dev/sdb1* to put the ldlinux.sys file onto my flash drive
4 - *syslinux -s /dev/sdb1* makes the flash drive bootable
5 - *mount -o loop /path/to/ubuntu8.04.iso /mnt* mounted the ISO to the /mnt directory
6 - make sure that hidden files are displayed in the /mnt directory (ctrl+h to toggle).
7 - copy all the files from mnt to the flash drive
8 - *sudo gedit /mnt/isolinux/isolinux.cfg* simply select save-as (no editing required for 8.04 supposedly, yet to test) and select to save it as syslinux.cfg in the isolinux directory of the flash drive.
9 - rename the isolinux directory of the flash drive to syslinux
10 - use

Like I said, I haven't tested this yet, but I will in the morning. This method yields a live-booting flash drive, but I'm fairly certain that I can adapt this method to fit my OSX application.

I think all I'll have to change is instead of step (7) I'll have to actually cp the directory with the extracted ISO files in it, and figure out what file is actually the boot file and edit my .cfg file accordingly.

I'll keep you updated, on this whether this method will work for me... but in the mean time, if anybody know's what I'm missing for the "wodim format as iso9660 and burn the iso directly" method let me know, because that seems as though it would be a much more repeatable method.

Thanks again

---

### Post by Loaded.len on 2008-08-24
A) If you use the -s switch for syslinux it will boot slower than the 2nd coming of Christ. (it's for older, weirder, not-so-supported BIOSes - used as a failsafe.)  The syslinux man pages say "safe, slow and stupid"

B) That method will not produce a "persistent" Live boot environment. (not sure if that's an issue for you)

C) That method (and others like it) will not always (read rarely) work without a modified version of initrd.gz, and some carefully selected boot options like root=/ 

I'm not saying it's a bad method by any means... Just wanted to make sure you understand the pitfalls.

---

### Post by CTRLurself on 2008-08-24
Well, my problem with Syslinux was that i wasn't sudo-ing it, i was just trying to run it - meaning i didn't have write access. Once i realized i just had to sudo syslinux, it worked straight away (no -s modifier)

and the 10 steps that i posted (while appearing to work) actually doesn't currently work, when I attempt to boot off it, it says that the partition table format is not recognized. So i think i'm going to redo the whole thing with the flash drive in fat16 instead of fat32 and see if that makes any difference.

the good news is, this time i can just format, mark as bootable, and sudo cp all the files right back onto it without any more file editing.

And I'm not worried about persistance because the end applications for this are actially very different from just making a USB live cd.

---

### Post by CTRLurself on 2008-08-24
Reformatting to fat16 was no help, it's the partition tables that are unrecognizable, not the format. and like I said at the begining of this, i need to keep this as simple as possible... so I'm attempting another somewhat more generic approach to see if it'll work

plug in flash drive it's located at /dev/sdb1 by default, unmount it, and reformat to ext2 (leave unmounted)

[I] sudo mkdir /mnt/iso
 sudo mkdir /mnt/sdb
 sudo mount -o loop -t iso9660 /path/to/file.iso /mnt/iso
 sudo mount /dev/sdb1 /mnt/sdb
 sudo cp -R /mnt/iso/* /mnt/sdb
 sudo umount /mnt/iso
[/I]

I then created a folder in my home folder (mkdir /home/josh/boot) and copied the vmlinuz, isolinux, and initrd.gz files to it, and then did

[I]
sudo cp -R /home/josh/boot
sudo umount /mnt/sdb[/I]

This effectively mounts the ISO to the /mnt/iso directory, and it mounts my flash drive to the /mnt/sdb directory. I then did a forced copy-paste from one to the other. Essentially burning the ISO file to the flash drive in iso9660 format as though it were a CD. Then i inserted a boot folder with the files that are likely to be the boot files (based on what I've read, now I need to figure our the GRUB menu setup required to make it boot on my system to test the install).

The next step will be applying syslinux to it so it can boot as a stand-alone device, but I need it bootable before i worry about making it bootable as a standalone device.

The flash drive appears to contain all of the files from the ISO and no errors popped up.

I edited GRUB to include the option to boot from my flash drive.

*sudo gedit /boot/grub/menu.lst* and inserted
title       Ubuntu flash drive
root       (hd1,0)
kernel     (hd1,0)/boot/vmlinuz root=/dev/sdb1
initrd     (hd1,0)/boot/initrd.gz

and i kept getting a "kernel must be loaded before initrd" error... so I'm fairly certain my kernel line is wrong, but I'm going to sleep now because I have class tomorrow, but I'll be working on this tomorrow during my break between classes. And I'll try to keep this thread up-to-date with my progress so if you have any ideas on what I'm doing wrong let me know because I check this thread pretty frequently.

---

### Post by Albert Net on 2009-12-14
If the iso file is linux OS, it is not so hard. Check the post

[http://ubuntuforums.org/showthread.php?t=1328650](http://ubuntuforums.org/showthread.php?t=1328650)

As for windows, I am still working on it.
No solution yet.

---

