---
title: "How to setup partitions for grub2 and distros"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by DAE of LINUX on 2009-10-15
*Ok, first post, deep breath, and pretend they are all naked.*

OK! I'll begin with a  bit of background on me, skip to the next paragraph if you don't care:  I started my Linux experience with Ubuntu 8, and while I could see many improvements over XP and Vista, the learning curve proved to be too steep and I went back to my comfort zone for awhile. Since then I've fried my newer awesome computer, and have revived my old computer, of which I do not intend to burden with the oversized resource hog that is Vista. I'm fed up with the hacked copy of XP that had been using due to security reasons and the date and time never being correct. So back to Linux, and so far Ubuntu 9 seems a bit friendlier. 

Here is my issue. I'm running the live CD and I started the install process. Windows is on a separate hard disk (Hey I still have games to play), and I want to install multiple Linux distros on my 160GB hdd, so naturally I have to partition it out. I want to set it up so that I have grub2 on one 8MB partition so that I can boot any OS from there and never worry about it getting corrupted. Then I want maybe 40GB for Ubuntu, maybe 40GB for Fedora (40 GB should give me enough room for the OS's and room to expand with more programs, right?), maybe 20GB for Arch Linux (I want to be a command line user some day), and the rest of the space can be used for a media storage partition, preferably NTFS so Windows can use it too.

So this was my intention:
sda1 - ext2 - ? - 8MB (GRUB2 partition)
sda2 - ext3 - ? - 40GB (Ununtu)
sda3 - ext3 - ? - 40GB (Fedora)
sda4 - ext3 - ? - 20GB (Arch)
sda5 - NTFS? - ? - 60GB (media)

I'd like to make them all primary but I know I'm limited to 4 primary partitions. What's the best way to handle that? And I'm not sure how to set up the mount points. /boot for the GRUB2 partition? 

Thanks guys, for taking the time to help.

---

### Post by ermeyers on 2009-10-15
Not answering your question directly , if you're exploring OSes, take a look a VirtualBox or another virtualization program in Ubuntu.  It might help you explore what you want to do, a different way.

---

### Post by ermeyers on 2009-10-15
Otherwise try making Primary sda1 [bootable] ext2 /boot part, and the others Logical sda5 etx3/ext4/NTFS parts, etc.

---

### Post by raymondh on 2009-10-15
To explore and learn OS', virtualization is great.

I am still trying to learn GRUB2 and I don't know how it interacts with other distros.  But to visualize your set-up:

/boot - primary
/data - primary
Extended
*Ubuntu - logical
*Fedora - logical
*etc  - logical
Swap

You may want to start reading (for reference) Herman's site about creating a separate boot partition

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

Cheers,

---

### Post by DAE of LINUX on 2009-10-15
Hmmm, I've just been reading up on virtualization and that does seem the best way to handle the other distros, and especially since I'm most comfortable with Ubuntu, I can easily switch back when I need to. So lets say I split the hard drive into three partitions, one for the grub loader, one for Ubuntu and VirtualBox, and one for the NTFS and media. That takes care of the 4 primary partitions limitation. How do I set up the mount points? 

And will the virtualbox really run OSes like they are installed indipendantly? I never had much luck with Wine but I get the impression that it's not the same thing.

---

### Post by kayvortex on 2009-10-15
The way to have more than 4 partitions is to create an "extended partition". This is a special type of partition that actually allows you to create lots of partitions -- more than 4, but less than 15, if I (probably don't) remember correctly -- within it. Most, if not all, disk partitioners will give you an option to create a primary or extended partition.

How you partition your disc depends on what's going in it: Windows needs to be on a primary partition, but Linux doesn't; so, if you are also going to, or may in the future want to, install Windows, then you should have a primary partition. (In fact, there's no harm in having a primary partition or two included in your partition scheme.) Otherwise, you can then just create an extended partition in the rest of the disc, and then create partitions within it for all your Linux distros. What you could do is this:

*Edit: sorry, about the "image" below, just press the "quote" button at the bottom of this post and scroll down the reply box that appears in order to see it as it's supposedd to look like.*
__________________________________________________________________________
|           |           | ______________________________________________ |
|           |           | |           |           |         |          | |
| PRIMARY 1 | PRIMARY 2 | |  DISTRO 1 |  DISTRO 2 |   ...   | DISTRO X | |
|  (sda1)   |   (sda2)  | |   (sda5)  |   (sda6)  |         | (sdaX+4) | |
|           |           | |___________|___________|_________|__________| |
|           |           |              EXTENDED PARTITION (sda3)         |
|___________|___________|________________________________________________|

And leave sda1 and sda2 for ntfs storage (leaving one or both for future Windows installations, perhaps).

Some other things: firstly, swap. You only need one swap partition for all your Linux distros, but if you ever hibernate a Linux system, it will write its memory to swap, which means that if you hibernate one Linux OS, booting *another* Linux OS may corrupt it.

The second thing is what is called a "dedicated GRUB partition": you will want to have this! Basically, every distro needs to have a /boot directory where the menu.lst is located, which tells the GRUB boot loader what to boot, and where it is. Having a separate partition for /boot that each distro shares is not a good idea because some may be very clumsy and not recognize the entries for the other distros. But, on the other hand, each distro needs to be included in a menu.lst file for it to be able to be booted by GRUB. What a dedicated GRUB partition will do is this: each distro will be completely installed in its own partition (i.e., no separate partition for /boot), and have no knowledge of any other distro. You will then create another small partition for *another* GRUB program that will simply point to each distro's /boot/menu.lst file. Take a look at [here]("http://www.troubleshooters.com/linux/grub/grubpartition.htm") for more info.

Lastly, a shared /home directory for each distro: you probably want your personal files to be accessible regardless of what distro you boot up. You can do this by having /home as a separate partition from the partitions where the distros are installed. Actually, I'd recommend you make the partition /home/*your_COMMON_username*/Desktop since /home will always contain config files that you will probably want separate for each distro. The "Desktop" folder, however, never contains system-specific info, so can be safely shared between disros.

Yeah, lots of research to do if you don't want to go down the virtualization route! Let me know if you have any questions.

---

### Post by DAE of LINUX on 2009-10-15
kayvortex, thanks for the awesome information on the dedicated GRUB partition. That'll come in handy. But, the Ubuntu live-cd doesn't give me the option for extended partitions, nor does it give me the option to format in NTFS, but I think I can change that later, maybe with gparted?

---

### Post by kayvortex on 2009-10-15
> **DAE of LINUX said:**
> kayvortex, thanks for the awesome information on the dedicated GRUB partition. That'll come in handy. But, the Ubuntu live-cd doesn't give me the option for extended partitions, nor does it give me the option to format in NTFS, but I think I can change that later, maybe with gparted?

Hang on, let me put a LiveCD in and let me take a look...

---

### Post by DAE of LINUX on 2009-10-15
I guess I could format as FAT32 for windows to detect it. What mount point do I use for the Ubuntu partition?

---

### Post by kayvortex on 2009-10-15
> **DAE of LINUX said:**
> I guess I could format as FAT32 for windows to detect it. What mount point do I use for the Ubuntu partition?

Right, OK, the Ubuntu partitioner seems pretty dumb. It's the "Logical" radio button at the top. Yeah, you can just specify it as anything really and just reformat it as ntfs with gparted later. In fact, you can boot up the LiveCD instead of installing Ubuntu, and start gparted from there and create your partitions with that. Gparted is a much better disk partitioner, and you can format partitions as ntfs straight away with that. Then, when you reboot and choose to install Ubuntu, you can just select the partition you want to install Ubuntu in rather than create it then and there too.

The mount point you want to use is '/' (just a forward slash).

---

### Post by oldfred on 2009-10-16
This is my entire menu.lst from my grub partition. I made it 120MB but only about a third of that is used.

More from Herman's site:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

Be sure to install Grub in every bootable partition. I did get warning messages not to install Grub2 in a partition as it has to use block something and it is not recommended for Grub2. It is just that is how all chainbooting works and I have had not issues with Grub2 in the Karmic partition.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default        1
timeout        10

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Grub Chainload Menu
root
title        -
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title       Ubuntu 9.04 Jaunty 32 bit @ sdb1
root        (hd1,0)
chainloader +1

title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1

title       Ubuntu 9.10 Karmic 64 bit @ sdc7
root        (hd2,6)
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

title   Reboot
reboot

title   Halt
halt
```

---

### Post by kayvortex on 2009-10-16
Note that GRUB 2 is a complete rewrite of GRUB and has different config file syntax (see [here]("https://wiki.ubuntu.com/Grub2") for some info). What you seem to have is GRUB Legacy (i.e., the older GRUB that has been the default for up to Karmic is released in about 2 weeks time); so, I think you can use GRUB 2 just as you are now using GRUB Legacy, but bear in mind that you are only using GRUB 2 for Karmic (I presume) and GRUB Legacy for everything else.

That message about being in the first 1024 cylinders is just for really old systems: you're likely to have no trouble with it.

But, it all looks fine. The GRUB data installed at the MBR should point to that GRUB partition, and any new OS installation should write their GRUB data to the installation partition and *not* the MBR, otherwise when the system boots, it will read that new installation's GRUB files, and not the ones in the dedicated partition. However, it's not hard to fix things if that does happen.
When a new OS is installed, simply boot into one of the other OS's, mount the grub partition (you should probably remove the dedicated GRUB partition from /etc/fstab if it's auto-mounted since you never normally need it mounted) and just add an entry to the OS like the ones in there already.

Let me know if you have any problems.

---

