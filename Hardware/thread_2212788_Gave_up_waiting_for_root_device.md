---
title: "Gave up waiting for root device"
date: 2014-03-23
forum: Hardware
---

### Post by teroot on 2014-03-23
[COLOR=#070F14][FONT=Verdana]Upon booting Ubuntu 12.04 as normal one day, I received a black screen stating "Gave up waiting for root device", and dropped into a Busy Box shell. I tried another cold boot and eventually managed to boot back into Ubuntu, but everything had a major lag. After several unsuccessful attempts to boot again, I attempted to re-install 12.04 and received the following message "error: no module specified; error: no suitable mode found; error: unknown command 'terminal'". I downloaded the 13.10 installation iso and tried to install it from a USB stick, it froze about 25% of the way through both times I attempted to install. I even went and tried a 10.04 installation CD and the installation failed, saying there was an error copying files to the hard disk because it was a read-only file system. I have used the disk partitioner in all 3 live CDs to reformat the entire HDD before each installation. At this point I can't think of anything other than a corrupted HDD. I have attempted multiple self tests on the HDD using SMART, but each time it says Self Test Failed. I don't know if that means the HDD failed, or the test itself failed. What's the best way to determine where my issue lies before I start throwing money at it? Thanks. [/FONT][/COLOR]

---

### Post by 23dornot23d on 2014-03-23
It appears to be pointing towards a problem with the hard disk ......... and as you have tried smartmon and the self test fails - it seems a good indication that is the problem ...........

If you can check the drive by running a version of Linux from a external source like a livecd or better still a flash drive you may be able to determine a little more by adding the following program to see if you can determine any faults with the structure of the disk - but use this with care too ..... its an advanced tool ........ in the wrong hands can cause more problems than good.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk may help give some more information on the structure of the hard disk - as it may be just that somehow the partition table 
has been corrupted - this may make it possible to recover the hard drive. ( but if the hard drive is on its way to failing - the main thing may be to get any valuable data off it - that is if you do not already have a backup ) now would be the time to get what you
can off of it.

The make of hard drive is it and what size ....... you do not say if its a Sata or ISA ... is it in a laptop - what type of ventilation - has it overheated or is it old ..... they are reasonably cheap to replace. ( when a hard drives fail - there is usually short warnings that let the user know ....... noise of the hard drive may increase and many errors to do with bad sectors can show up )

Hope this helps in some way .......... if its a laptop ...... what I have done on one of my machines was to completely remove the laptop hard drive and boot from a external USB drive . ( depends on what machine it is here and how easily available the replacement hard drive is for the machine in question )

Hope something helps ........ how old is the drive ? is there important data on it that you have not managed to retrieve - photos
documents etc ...... photorec [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) may help in some cases but you still may need a external drive to put a backup onto ........

---

### Post by ajgreeny on 2014-03-23
It may be worth using the live CD or USB and running ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition's device name.

---

### Post by teroot on 2014-03-30
Sorry for the lack of background info on the drive. It's a WD5000AAKX SATA drive in a desktop. Manufactured Dec 2011. I've already recovered all the information I needed off of the drive using a Live USB drive with Ubuntu 13.10 on it. I used the Live USB to format and install 13.10 on the entire drive, it ended up taking approximately 15 hours total. Upon trying to boot, GRUB came up immediately, giving me the option to boot into Ubuntu, Ubuntu recovery mode, or the MemTest. I first tried to boot normal into Ubuntu, it came to a blank loading screen and I gave up after 20 minutes. I tried to run e2fsck from the recovery mode and it froze as well. I have a feeling if I let Ubuntu load, it would eventually get into the desktop environment, but would run extremely slow. I changed the physical SATA cable running from the HDD to the motherboard and tried different connections on the motherboard, to no avail. I can mount the HDD from the USB and read and write to it, but I can't boot into it. I ran e2fsck in the Live environment on the partition and it checked out clean. It appears to have been formatted properly with a 4GB extended and swap partition, 1 MB of free space and the rest as ext4 filesystem. Any other ideas? Thanks for the help so far!

---

### Post by slooksterpsv on 2014-03-30
If you have all the data you need backed up I'd use gparted and wipe the drive and recreate the partition table scheme if you're using MBR or GPT. 

If you have Windows on the computer that's a different story as you'd want to:
1- Backup all the windows data
2- Create recovery media for your Windows portion of your computer (e.g. if its HP run the HP Recovery media software)
3- Reinstall Windows if you need it, and wipe the entire drive delete every partition etc.
4- After installing Windows, resize the drive using diskmgmt.msc and make a partition for Ubuntu
5- Reinstall Ubuntu.

---

