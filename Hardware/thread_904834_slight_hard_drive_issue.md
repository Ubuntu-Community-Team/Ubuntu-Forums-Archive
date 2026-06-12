---
title: "slight hard drive issue"
date: 2008-08-29
forum: Hardware
---

### Post by scalywag66 on 2008-08-29
I have a slight problem with not being able to mount/view the hard drive that is actually holding the partition that is running Ubuntu.

The PC I'm testing Ubuntu on first before I actually install it on the other pcs, has 80GB of hard drive space, but supposedly has 2 hard drives. I say supposedly 2 hard drives because on a couple times that I had to do System Recovery on this machine, it would ask me before finalizing the recovery process if I wanted to keep:

C: at 30GB & D: at 50GB,

or if I wanted to change the hard drive space between the two drives, which made me think, "shouldn't the memory be dedicated for each drive instead of being interchangeable?".

So anyways, since D drive has more room, I made the Ubuntu partition to be on D drive.  On Ubuntu, I am able to explore C drive with no problem, but can't see the rest of the D drive that isn't partitioned, and I have some applications on D: that I would like to test with Wine. 

Any idea on how to mount the rest of D: and why I can't see it?

---

### Post by nicedude on 2008-08-29
The PC I'm testing Ubuntu on first before I actually install it on the other pcs, has 80GB of hard drive space, but supposedly has 2 hard drives. I say supposedly 2 hard drives because on a couple times that I had to do System Recovery on this machine, it would ask me before finalizing the recovery process if I wanted to keep:

C: at 30GB & D: at 50GB,

THIS IS JUST ONE PHYSICAL DRIVE WITH 2 PARTITIONS SETUP

or if I wanted to change the hard drive space between the two drives, which made me think, "shouldn't the memory be dedicated for each drive instead of being interchangeable?".

NO  SINCE IT IS ONE DRIVE AND IT HAS 2 PARTITIONS

So anyways, since D drive has more room, I made the Ubuntu partition to be on D drive. On Ubuntu, I am able to explore C drive with no problem, but can't see the rest of the D drive that isn't partitioned, and I have some applications on D: that I would like to test with Wine. 

IF IT IS DRIVE D IN WINDOWS THEN IT IS PARTITIONED

Any idea on how to mount the rest of D: and why I can't see it?

THIS MAKES NO SENSE AS IF YOU CAN BOOT UBUNTU THEN ITS PARTITION IS MOUNTED AT THAT TIME

You see a physical hard drive can have 4 primary partiitons and unlimited extended ones inside one of the primaries if you want, I would bet you have more than 2 partitions already though since if you have windows there is one and if you have Ubuntu then it will have a SWAP & System partition and you could also have more but 3 would be the minimum you have already. Try running the following command to list your disk partition tables and post the putput here for me to see and I can tell you what is going on with your PC.

sudo fdisk -l

And that is a lower case L as sometimes it looks like a one :-)

Post that output and I will help you figure it out.

---

### Post by scalywag66 on 2008-08-29
[quote="Scalywag66"]Any idea on how to mount the rest of D: and why I can't see it?

[quote="NICEDUDE"]THIS MAKES NO SENSE AS IF YOU CAN BOOT UBUNTU THEN ITS PARTITION IS MOUNTED AT THAT TIME [/quote][/quote]

That's exactly what's throwing me off.   I only dedicated about 10GB from D: (I know, waaaay to small) since C: is damn near full.  I can see C: and the 'File Disk' drive Ubuntu is partitioned on D:, but not the remaining unparitioned files.

In any event, the output that command you provided reads as:

[quote="RootTermina"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf18342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1462    11743483+   7  HPFS/NTFS
/dev/sda2            1463        9729    66404677+   f  W95 Ext'd (LBA)
/dev/sda5            1463        9729    66404646    7  HPFS/NTFS [/quote]

---

### Post by nicedude on 2008-08-29
As I thought you only have 1 hard drive and it has been partitioned with 3 partitions but none of them are Linux partitions, I will break down what these are. I am now assuming that you are running Wubi which is not a real Ubuntu install but a way to install Ubuntu and run it from within Windows, which is not the best for performance

The SDA is one physical hard drive each sda1 2 & 5 are partitions on this disk.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1462    11743483+   7  HPFS/NTFS <- this is your C drive in windows

/dev/sda2            1463        9729    66404677+   f  W95 Ext'd (LBA) This is just an extended partition which is a data container for other partitions

/dev/sda5            1463        9729    66404646    7  HPFS/NTFS <- This is a NTFS data partition within sda2 and looks like it takes up all of sda2's space


Man I hate to tell you a solution that is some work ( but not hard if you follow directions ), but I also don't want to not give you the best advice. If this was my box I would delete sda2 and sda5 using a live Ubuntu CD using the partitioner and then after a reboot I would install Ubuntu using the same live CD giving it 20GB for its system and 2GB for a SWAP partition and once the install is finished you could reboot into ubuntu and partition the rest of the 40GB or so of free space as NTFS or FAT32 and use it as a data partition which you could access from Ubuntu or XP. This would give you the best and fastest Ubuntu possible and would be superior to Wubi Ubuntu which is not as fast since it is running inside windows.


Google XP Ubuntu dual boot and you should find all kinds of nice guides that can explain this more or help you do it step by step. Trust me this is the best bet for you :-)

Goodluck

---

### Post by scalywag66 on 2008-08-29
lol

I guess I have to get my "4:20" ready for the night cause that sounds like some work!!! 

I'm still very new and learning the ropes to this new OS and the ups and downs to dual booting/swapping etc., so I'll be asking quite  bit.  Currently when it boots up I get 15 seconds to choose between XP or Ubuntu and since I lost internet capability on XP but am able to get online on Ubuntu, here I am.

So I'm wondering if I should've listen to my first instinct, which was to burn the installation as .iso image on a cd and install that way, but wasn't sure if it would work in DOS mode on cd boot-up, or if I had to do it Windows XP, so I just extracted and installed as it was.

---

### Post by nicedude on 2008-08-29
You should burn the Ubuntu iso to a CD and it will boot up into a full graphic environment just like Ubuntu in wubi and you can install it with nice GUI etc. If for any reason the live CD does not boot for you then they have an Alternate one that does boot to a text based installer but it is just as easy to install that way too, but I bet the Live CD will boot up for you. In fact you should try it out first, just burn the ISO to a CD and try to boot with it and see if it works.

Would say roll a 4:20 for me but I have a job interview next week and probably have to stay 4:20 free for another week :-(


Take it easy and try the live CD, if you need help doing the dual boot setup I will be glad to help you with it just PM me when you have some time to do it :-)

Nicedude

---

### Post by scalywag66 on 2008-08-30
Well here I am, I'm on the Live CD environment and was about to install, but wasn't sure about the partitioning part so aborted the actual BIOS installation thingy.  

The pc is Sony VAIO with VAIO System Recovery Discs(no actual MS Windows XP from purchase) that completely reinstalls Windows if you use Full System Recovery option, but I lost the damn discs and since I don't have any kind of copy of Windows XP on CD to reinstall if all goes haywire, here's where my concern came.......

do I do the Guided partition, or the Manual?

The actual sizes of the current drives are different from the last time I did a recovery.  

```
 total space  -    avail
C:  12GB          1.67GB
D:  68GB          50.3GB
```What I want is 30GB  off of D: for Ubuntu and keep the rest as is for both C: & the rest of D: (important files on D: space that's already used).

Will the Guided partitioner resize all of C: and D: if I use it and make me install Windows XP again, losing everything?  Cause  again, I have no XP disc and am screwed if I mess it up bigtime.

However, if I go Manual, what do I name the type of partitions for D: (or sda2/5, er whatever), since I'd like....
```
30000MB (for Ubuntu) *partition type?*
2000MB    (for swap) *partition type?*
```???

Is SDA 2 D drives freespace, or is that SDA5 ?   Or am I completely off!?!?(in which case, LuLz!)

---

### Post by nicedude on 2008-08-30
There are 2 kinds of disk partitions in PC hard drives first is primary partitions of which you can have up to 4 of them then there are extended partitions which are just containers that can contain other extended ones ( this lets you have more than 4 partitions total ) sda2 is an extended partition and sda5 is contained inside it ( so if you delete sda2 you would destroy sda5 as well since it is inside sda2 ). But here is what you need to do to do what you want.

First you will need to boot the live CD and don't go to install but instead go to System -> Administration -> Partition editor and use it to resize sda5 down to 30GB which would leave you 30GB for Ubuntu. After that reboot with the live CD again so the changes to the hard disk partition tables take effect ( this is important ). Once rebooted now you can select install and choose manual partitioning when you get to that point ( now you wont have to tell it what sd? you want to make the 2 partitions we need to create it will do this for you ). In the partition editor select to make a new extended partition in sda2 and make it 2GB and set it to format as SWAP then you are done with that one, now make another extended partition in sda2 and use whatever space is left free for its size and set it to format it as EXT3 and in the mount point box put / which means root ( this is even the first choice in the mount point drop down box ) and your done click to continue the install and it will install ubuntu the rest of the way and when it is done installing reboot again and you will have a grub boot menu with both Ubuntu & Windows listed and your done :-)

Hope that is easy to understand but if not PM me and I will try to explain more later but I have to go run some errands and it might be later tonight before I can get back to you.

---

### Post by scalywag66 on 2008-08-30
It's all gravy!!! [IMG]http://www.systemwars.com/forums/images/smilies/icon_smile.gif[/IMG]

I think......

[IMG]http://www.systemwars.com/forums/images/smilies/indifferent-blink.gif[/IMG]

I uninstalled Ubuntu and reinstalled with Live CD after burning the iso to a disc.   As would be expected, you are correct about Ubuntu running much faster.  

C: size is the same  
D: (XP)        28GB
D: (Ubuntu) 40GB

However, the problem with being not able to see/mount 'D: (XP)' still remains.  Why would that be? 

Thanks a lot to everyone who helped!!!

[IMG]http://www.systemwars.com/forums/images/smilies/icon_smile.gif[/IMG]

---

### Post by nicedude on 2008-08-30
For a permanent every boot solution it needs to be added to a file called fstab but you can learn that later and instead just use the following command to install a program called pysdm which will mount disks for you.


sudo apt-get install pysdm


and to run it after install

sudo pysdm

then select the drive and partition on the left hand side of GUI window and then press mount and bam it should be mounted :-)

Hope this helps

---

