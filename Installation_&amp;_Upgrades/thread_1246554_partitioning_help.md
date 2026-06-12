---
title: "partitioning help"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by PowerSource on 2009-08-21
I'm trying to install ubuntu server edition 8.10 on a computer that i just got from my dad's work. It currently got windows xp installed but we don't know the password. My dad isn't allowing me to remove xp so i will have to install ubuntu on a new partition. but the partition manager in the installer isn't the easiest to use. the option that seems the most right says something like this when translated: "guided-change size on (blabla) partition 1 (sda) and..." and then i can't see the rest of the line.
so i guess my options are these:
*choose that option and hope the best.
*download a live cd and make a new partition through that and then install it on that one.
*download the 9.04 disk and hope that it's more user friendly.

---

### Post by starcraft.man on 2009-08-21
Word from the wise. Partitioning ain't meant to be easy. Easier it is to partition, easier it is to wipe all your data out in seconds. Seen enough people cry after automated installer.

My advice, download the 9.04 live cd and then while booted into it, go to gparted. System > Admin > gparted. Then partition as ya like new section. For more info, see [here.]("http://gparted.sourceforge.net/documentation.php") Read the old section, going down, when your done if you've any questions post back. I'll agree the installer partitioner is kinda useless.

Ask questions before you make permanent changes to partitions. Also, backup any life or death data, you been warned.

Edit: Oh and yes, as herman noted, I'm not sure why ya want to install a server edition. For general use, that's not advised, not by me at least.

---

### Post by Herman on 2009-08-21
You don't need to know any password to get into XP, just press F8 while it's booting up to boot into safe mode, then change the password and reboot.

But your idea to put Ubuntu in is a good one, but it sounds like maybe you have a problem with your display if you can't read the text boxes. Something like that used to happen to me with my widescreen laptop in older versions of Ubuntu, but I cheated by looking at the illustrations in my website to see what to do and counting the number of times I pressed the tab key to highlight the right choices as they were not showing on my screen.

How come you want Ubuntu Server? I don't think there's any GUI in it, I think it's only a command line system, are you sure that's what you want?

I'd be inclined to advise you to go download Jaunty Jackalope 9.04 'Desktop' Live/Install CD, that will probably suit most people better, unless you really want to install a server for some reason. And you might be right, it probably will be more user freindly too. If you're lucky, the installer might show up in your display better but I'm not sure, that depends on what the problem is.  :)

---

### Post by Kat_129 on 2009-08-21
hey,
I am not exactly sure what are you doing. But I would suggest you to do it manually partition the drives. And you don;t need to know the password for you Windows XP. 

Here is one of the  site that I used for my research before installing it. [http://www.linuxconfig.org/How_to_dual_boot_Windows_XP_and_Ubuntu_Linux#Create_a_new_partition](http://www.linuxconfig.org/How_to_dual_boot_Windows_XP_and_Ubuntu_Linux#Create_a_new_partition)
Also, dont touch the C:and the D: ,  use the free space to create the new partitions.
 
Good luck!

---

### Post by PowerSource on 2009-08-22
you seem confused by that i use the server edition.
it's because it's gonna be a server :P

---

### Post by Herman on 2009-08-22
:) Oh, okay, very good! I was worried about that. Just as long as you know what you're doing that's fine.

Here's a link I found in Ubuntu Community Docs that might help you to boot your server CD with kernel options that might suit your monitor better, [BootOptions]("https://help.ubuntu.com/community/BootOptions"). 

Here's another link that you may find informative, [HOWTO: Change bootup and console resolution]("http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters") - Indras - Ubuntu Web Forums. 
You may be able to use the boot option 'vga=ask', I'm not sure, but it might be worth a try.

---

### Post by rsrini on 2009-08-24
Hi, I am a new user to Ubuntu. I am trying to install 9.04 on new 500GB HDD. I made first primary partition as 12GB for Windows C. Then made 150MB /boot primary. Third 2GB primary for swap. After wards made three 12GB extended partitions for three linux roots. Remaining unallocated partitions showing as 416GB. But i am unable to make any partition on that unallocated space. The SDA4 showing as extended is 36GB only. I had installed ubuntu 9.04 on SDA6, Suse on SDA5 and Fedora on SDA7. Help me now how can i make partition for Windows D, and common data space for Linux from the unallocated. 

It is telling unable to create more than 3 primary partition. Even it is not allowing to create extended partition. It is greyed out all the options.

R.Srinivasan.

---

### Post by Herman on 2009-08-24
:) Hello rsrini,
You need to make your extended partition bigger so you can make more logical partitions inside it.
You already have three primary partitions plus one extended primary partition, that makes four and that's all the primaries we're allowed. 
However we can make quite a number of logical partitions in the extended, so if you make that bigger you'll be able to make more partitions inside it.

Regards, Herman :)

---

### Post by rsrini on 2009-08-24
> **Herman said:**
> :) Hello rsrini,
You need to make your extended partition bigger so you can make more logical partitions inside it.
You already have three primary partitions plus one extended primary partition, that makes four and that's all the primaries we're allowed. 
However we can make quite a number of logical partitions in the extended, so if you make that bigger you'll be able to make more partitions inside it.

Regards, Herman :)

Hi Herman,

I already made three extended partitions on it (12GB each) and installed ubuntu, fedora and suse. Now i am not able to resize or partition the unallocated space. The details are
1. sda1    12GB     WindowsC    Primary
2. sda2    150MB    /boot           Primary
3. sda3     2GB      swap            primary
4. sda4    36GB                        Extended
5. sda5     12GB     /root-suse    (i don't know whether it is logical or )
6. sda6     12GB     /root-ubuntu   (i don't know whether it is logical or )
7. sda7     12GB     /root-fedora    (i don't know whether it is logical or )
8. unallocated 416GB                 free space

Do i need to delete all the three root partitions and create one bigger (remaining full size) extended partition. The gparted tool not giving option to resize the sda4 or the last one. It is not allowing to resize the sda7 to include the remaining unallocated free space.

R.Srinivasan.

---

### Post by Bartender on 2009-08-24
I think the OP is biting off more than he can chew.

---

### Post by Herman on 2009-08-24
> Do i need to delete all the three root partitions and create one bigger (remaining full size) extended partition.No, you should not need to delete any of the partitions you have already made.
>  The gparted tool not giving option to resize the sda4 or the last one. It is not allowing to resize the sda7 to include the remaining unallocated free space. Are you sure? The extended partition, /dev/sda4 is like a box with the three logical partitions inside it. 
You have given me the information that your extended partition is 36 GB and contains 3 logical partitions of 12 GB each. There is 416GB of free space following the extended partition. You need to resize your extended partition so you can create more logical partitions inside it.
If the option to resize the extended partition is greyed out, I can only think of one possible reason for that, one of your logical partitions is mounted and in use, therefore your extended partition is mounted too, which means you are not allowed to make any changes to it and that's probably why the option is greyed out.
Are you using  live CD or are you trying to do this work from within one of your installed operating systems? 
If so, try using a Live CD to do work on your hard disk with so the hard disk won't be in use at the same time as you are working on it. Your Ubuntu 'Desktop' Live/Install CD Live CD should have GParted in it if you it. Otherwise you can get GParted in many other Linux live CDs, the most advanced one is Parted Magic nowadays, a very nice and useful distro. It's best to use a Live CD or a USB or something on another disk of some kind so your hard disk partitions won't be mounted. I'm only guessing that might be your problem. 
Regards, Herman :)

---

### Post by rsrini on 2009-09-19
I had done repartition. Deleted all the Linux partitions including swap. Only kept the Windows partition SDA1 and boot partition SDA2. Made all the remaining whole space as extended partition SDA3. Inside SDA3 (starting from SDA5) made all the logical partitions. 3 linux roots, one swap, one home etc. Reinstalled all the linux os again. Now everything is fine. Thanks for support.

R.Srinivasan.

---

