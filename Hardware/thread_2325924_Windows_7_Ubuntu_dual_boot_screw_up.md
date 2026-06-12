---
title: "Windows 7 Ubuntu dual boot screw up?"
date: 2016-05-26
forum: Hardware
---

### Post by Nathan_Roach on 2016-05-26
[COLOR=#000000][FONT=verdana]Hello all,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]So a colleague of mine was hoping to set up a windows 7 and Ubuntu dual boot on his Dell Inspiron N7010. He's hoping to do some Unix scripting and decided this was the best approach. He asked me to help him with the install, which I did, and I'm now concerned that I may have bricked his computer.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]He's running Windows 7, so I partitioned the harddrive and allocated ~150Gb to the new partition. Then I downloaded the latest ubuntu .iso file, downloaded the universal USB installer found here:[/FONT][/COLOR][Universal USB Installer – Easy as 1 2 3 | USB Pen Drive Linux]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

[COLOR=#000000][FONT=verdana]and used it to mount the .iso file on to the partition I had just created with the option to format the drive turned on.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Seemed to perform the mount fine, but upon turning the system off and turning it back on the entire computer is booting to a black screen with a flashing underscore cursor in the top left corner. Booting to BIOS and running diagnostics gives me the error code 2000-0146. I did some googling and this seems to indicate a failure of the harddrive at some level. At this point I'm concerned I've bricked my co-workers computer and theres no way to fix this.[/FONT][/COLOR][IMG]http://www.techsupportforum.com/forums/images/smilies/new/hide.gif[/IMG][COLOR=#000000][FONT=verdana]Do any of you have any insight?[/FONT][/COLOR]

---

### Post by yancek on 2016-05-26
> [COLOR=#000000][FONT=verdana]He's running Windows 7, so I partitioned the harddrive and allocated ~150Gb to the new partition.[/FONT][/COLOR]

Better to simply resize (shrink) the windows partition and just leave unallocated space.  Pointless to try creating a partition for any Linux system from windows as a default windows system is totally incapable of even reading a Linux filesystem much less formatting a partition with one.

> [COLOR=#000000][FONT=verdana]and used it to mount the .iso file on to the partition I had just created with the option to format the drive turned on.[/FONT][/COLOR]

I'm not sure if this is a question of termnology here but, the UUI software is used on a windows system to put a Linux iso file on a flash drive and make it bootable.  You then use the flash drive to install Linux.  If you formatted the 'drive', that's the entire hard drive.  I'm not really sure what you did, you can do a frugal install which means using the software to put the iso on a partition and boot from it but I don't know that UUI can do that.

I guess the basic question is, did you actually put the iso on a flash drive with Ubuntu on it or do you have some other Linux system to use?

---

### Post by Nathan_Roach on 2016-05-26
> **yancek said:**
> 
I'm not sure if this is a question of termnology here but, the UUI software is used on a windows system to put a Linux iso file on a flash drive and make it bootable.  You then use the flash drive to install Linux.  If you formatted the 'drive', that's the entire hard drive.  I'm not really sure what you did, you can do a frugal install which means using the software to put the iso on a partition and boot from it but I don't know that UUI can do that.

I guess the basic question is, did you actually put the iso on a flash drive with Ubuntu on it or do you have some other Linux system to use?

Yeah so I think I used UUI to put it in the hard drive partition that I made. I do have other systems I can use, and I can get a ubuntu or windows copy on a flash drive if it will help.

---

### Post by yancek on 2016-05-26
If you can put an Ubuntu on a flash drive and boot it, do that and to get some information to post about drives/partitions, open a terminal and run the two commands below:

> sudo fdisk -l
sudo parted -l

Lower case Letter L in both commands.

---

### Post by colby8 on 2016-05-28
To recover windows you need to change the boot (or active) partition back to what it was (assuming the other partitions were not deleted), probably a somewhat small partition was what is used to be if it is a 64bit windows.  If you have a windows 7 install DVD or can put that on a flash drive it might repair it automatically for you.  If not you would need to use the advanced menu to change the active partition.    

BTW I suggest you install Ubuntu as a virtual machine, it should be easier and less likely to mess up the machine;)  Try virtualbox if you need a good free one.

---

