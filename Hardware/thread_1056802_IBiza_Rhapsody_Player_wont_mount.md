---
title: "IBiza Rhapsody Player wont mount"
date: 2009-02-01
forum: Hardware
---

### Post by akrobert on 2009-02-01
Hello
Im new to Linux and Ubuntu. Ive been running it about a month and a half and have enjoyed learning how to work with it, but I have an issue I cant seem to resolve on my own or with manuals or google or searching the forum so here goes. Any help is appreciated. 

I have an Ibiza Rhapsody Player. 30GB model. When I plug it in it comes up as idg1 and will not mount it. I tried going to the Storage Device Manager and it didnt even see it. I did 

Sudo Nautilus and there I could see it but I couldnt get it to mount. It gives me an error saying it cant special mount this device. If I go into the media folder where all the jump drives, my Ipod, and ext hard drives are its listed but I cant mount it from there either. I went to Ibiza's site looking for contact info and they dont say a word about using it with linux. Is there any way I can get this device mounted?

Thanks
Robert

---

### Post by ajgreeny on 2009-02-01
With your IBiza attached to the computer open a terminal and run ```
sudo fdisk -l
```(that is a lower case L at the end, not 1) and report back the output from that.  It should show the players device name and show the filesystem etc etc of that device which may help to get it mounted, or see what is going wrong.

You could also try adding the disk-mounter applet to your panel and see if that will mount it.  This is how I tend to do all disk mounting operations, rather than letting them mount at boot time;  I like to keep my OS partitions, Ubuntu, Windows and Linux Mint separate from each other, and see no reason to mount everything when I boot the computer.

---

### Post by akrobert on 2009-02-01
Thanks for the reply. Where would I get the mounting applet? like I said Im new at this. Though am really enjoying it and not missing windows..here is what it says

> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7         398     3148740    b  W95 FAT32
/dev/sda3   *         399       38505   306094477+  83  Linux
/dev/sda4           38506       38913     3277260    5  Extended
/dev/sda5           38506       38913     3277228+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
Note: sector size is 4096 (not 512)

Disk /dev/sde: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30019   156093788    b  W95 FAT32

thanks
Robert

---

### Post by ajgreeny on 2009-02-01
According to that you have three disks, sda - 320GB, sdb - 1000.2GB and sde - 159.8GB.  sda is your original disk with windows and your linux install on it, sdb also has a linux filesystem on it and sde, which could be your player, but is 160GB approximately is fat32, which most music/mp3 players are.

Do you think I have got that right?  Do you have two hard disks in your machine?  If so the sde is definitely your IBiza player.  If you have three hard disks then fdisk has not seen your music player and I don't know where to go from here.   However, to get the Disk-mounter applet, right clicking in an empty part of the panel and chose "Add to Panel"  Find the disk mounter and click add.

---

### Post by akrobert on 2009-02-01
hello

Sda1 is the /media/dellutility drive..for if I ever need to reinstall from scratch...was thinking I can probably wipe that one off too but was keeping it as kind of a failsafe in case I ever do something that terminally wastes my system and I need to reinstall and cant find a disk...

sda 2 is the OS mount it created when I upgraded from ubuntu 8.04lts which my computer came with to 8.10. its unmounted and I was doing to wipe it out...but wasnt sure if I should or might need it later down the road.

sda3 is the primary hard drive 291gb out of a 320gb drive
4 and 5 are just swaps on that hard drive

the Ibiza Rhapsody doesnt show up as any sda number...when I plugged it in under /media 3 new drives appeared, sdf1, sdg1, sdh1, when I did a "sudo nautilus" it showed a new drive sdf1 and said special drive sdf1 could not be mounted. cant mount it as me..and I cant even mount it as root..and when I unplug it the player says checking drive structure..so its trying to do something. If I plug it into a Windoze system its right there under my computer and I can drop and drag from and to it.

Thanks
Robert

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 7 398 3148740 b W95 FAT32
/dev/sda3 * 399 38505 306094477+ 83 Linux
/dev/sda4 38506 38913 3277260 5 Extended
/dev/sda5 38506 38913 3277228+ 82 Linux swap / Solaris

---

### Post by ajgreeny on 2009-02-01
OK, baffling.  Try running partition editor from the live CD, or even your ubuntu install, if you prefer, and see how that shows the IBiza player, if at all.

You don't say what the sdb is on the machine, only what the partitions on sda are, and I am a bit uncertain about your sda2, which you seem to suggest is a linux partition.  As it is a fat32 filesystem, I don't think it can be.  I assume you have windows on there somewhere, and it looks as if sda2 is that.  Am I right, and what are sdb and sde, which you have not mentioned?

---

### Post by akrobert on 2009-02-01
the partition editor doesnt show it at all...nor does storage device manager.

Ill give you a rundown of what I get when I do a sudo nautilus

sdb1 is my 1tb external drive ext3
sdd1 is a jump drive 16gb fat32
sde1 is my ipod 160gb ipod classic

when the ibizia is plugged in it shows as sdf1 but it shows only with an sudo nautilus which is unable to mount it and gives the error "unable to mount sdf1" second line "mount: special device /dev/sdf1 does not exist". If I look at the ibiza screen it says "Connected to Computer. Disconnect at Any Time:" which is what it always says when I have it plugged into a windows machine.

The only place I can see the device is when I do a sudo nautilus and then I cant do anything with it. I just can see that its there. If I go into the /media folder I see an sdf, sdg and sdh drive but all of them are empty and are not the drive and are unmountable also. It almost behaves as a device that is locked into only being used in windows somehow but I dont know how that could be since nothing else Ive ever run into is. believe it or not my ipod runs better under unbuntu than it ever did under XP or Vista. Pretty much everything does. Plus I read several articles where they were talking about an Ibiza 30 GB player that they are making that is for linux friendly and everything so its kind of odd that this one cant be used at all in..

Do you think its possible that this is a "windows only" device? didnt know there was such a thing but....

Thanks
Robert

---

### Post by ajgreeny on 2009-02-02
Stranger and stranger.  Sorry, but I'm out of my depth now and I don't have any more ideas.  I hope you get it sorted in some way.

---

### Post by akrobert on 2009-02-02
I appreciate your help
Robert

---

### Post by akrobert on 2009-02-02
Hello
someone recommended I use terminal and do a

> watch 'dmesg|tail'

with the player plugged in...the result it came up with was when I plug it in it says 

> new high speed usb device using ehci_hcd and address 5
configuration #3 chosen from 1 choice
reset high speed usb device using ehci_hcd and address 5

the reset line it does over and over and over

if anyone has any ideas Id appreciate it
Robert

---

### Post by mike-g2 on 2010-11-03
I realize this is a rather stale thread, but I've picked up one of these. I was wondering if you ever got yours to mount and, if so, how?

---

