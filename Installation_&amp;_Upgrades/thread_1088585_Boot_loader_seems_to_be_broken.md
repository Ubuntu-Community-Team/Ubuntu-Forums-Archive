---
title: "Boot loader seems to be broken"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Ian222 on 2009-03-06
I recently bought a used 64-bit AMD desktop that had Vista installed. I installed Ubuntu 08.10, updated, then partitioned the hard drive, then tried installing Vista. Vista wouldn't install (couldn't find a drive that met its requirements or something of that sort). I haven't been able to open Ubuntu since. I tried to format the hard drive, but it still doesn't work. I switched the hard drive with one that has XP and Ubuntu dual-booted. Grub starts and I can select which operating system to use. If I choose Ubuntu, I get an error,"kinit: No resume image: doing normal boot ..." and I get to a black screen where I can login with only a text interface. So, I assume something more serious is wrong. I would appreciate any suggestions. Thanks,

Ian

---

### Post by balaknair on 2009-03-06
As far as possible, always install the Windows OS first and then install Ubuntu if you want a dual boot setup. Windows needs to be installed to the first primary partition, and it overwrites the master boot record to install only its own bootloader.

To repair your Ubuntu(or Windows) installation, try Super Grub disk
Illustrated guide here
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

Edit: I think this might have to do with Ubuntu being unable to find your Swap partition

Could you post the output of this command *fdisk -l*

---

### Post by balaknair on 2009-03-06
I think I found something that might help here

[http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/)

---

### Post by Ian222 on 2009-03-06
Thanks, but this doesn't work. If I use Super Grub, when it tries to run Ubuntu, I get the message "Error 13: Invalid or unsupported executable format."

When I press esc to get to the Grub menu and select the recovery mode option the last line reads "9.622238 sd4:0:0:3: Attached scsi generic sg5 type 0

When I type sudo fdisk /dev/sda, I get the error "/bin/sh: sudo not found"

I tried using the Ubuntu cd and the commands in:[http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/)
They seemed to work, but now when I start the computer it says there is no boot media.  I tried re-installing Ubuntu, but it doesn't finish loading and I get a screen with a command line with ubuntu@ubuntu:
I tried fdisk -l from here, I get the error "cannot open /sda/dev"

Any suggestions as to what to try next? Thanks again.

---

### Post by balaknair on 2009-03-06
Try testdisk, it's a great little CLI app that you can install while running off the LiveCD, and has saved my bacon more than once.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Boot into Live CD--> once at the desktop, install testdisk( *sudo apt-get install testdisk* )

Run testdisk- In a terminal, type sudo testdisk--> Choose option 'Create'--> Choose the device--> Choose option 'Intel'--> Choose 'Analyse'--> You get a list of partitions found--> Press 'Enter' to continue if you think all the partitions have been found, or else choose 'Search' to see if testdisk can find more partitions; once you have the partition table ready and no errors are seen--> Choose option 'Write'--> Confirm Y/N by choosing Y and pressing 'Enter'.

Check the link above for more information on using testdisk. It's a fantastic tool and hasn't failed me yet.

---

### Post by Ian222 on 2009-03-06
Thanks, but I can't boot into the LiveCD. That's one of my problems. It doesn't finish loading and I get a screen with a command line with ubuntu@ubuntu:

I couldn't install the script from there; I get the error "E: Couldn't find package testdisk"

Any other ideas? Thanks.

---

### Post by balaknair on 2009-03-06
I think you should take a look at the hardware on this machine, especially the RAM. Maybe you could run a memtest off the LiveCD? Or perhaps swap the RAM chips currently in the machine with another chip that you know works for sure. Could be a reason for the Ubuntu Live CD not working.

Back to the non-bootable hard drive:
Can you remove the hard drive and attach it to another machine(on which you can install testdisk)? That's what I usually do(the LiveCD method I reserve for laptops).

You can also try one of the following:

1) Run Ubuntu off a USB startup disk(provided you have a USB drive with  enough space and another machine with Ubuntu on it).

2) Create a Testdisk Live CD
[http://www.cgsecurity.org/wiki/Create_a_TestDisk_FreeDos_LiveCD](http://www.cgsecurity.org/wiki/Create_a_TestDisk_FreeDos_LiveCD)

3) Use an alternate rescue CD like
ultimatebootcd [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)
Ubuntu Rescue Remix [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)
Gparted LiveCD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

These already contain the testdisk application on the CD(along with a whole lot of others), and all run off USB flash drives as well(and need less space than a full Ubuntu disk). But remember these are command line tools(except GParted).

4) Try using a different version of Ubuntu(for the Live CD), that sometimes works for me.

---

