---
title: "Thinkpad - Ubuntu Breezy Dual Boot Questions"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by justask on 2006-01-17
My T42p running Windows is currently partitioned as follows:

   C:  20GB Primary  - WinXP ntfs
   D:  20GB Logical   - Data  ntfs
   E:  12GB Logical   - Data  ntfs
   *    5GB Primary   - Hidden Recovery 

Is it possible to install Ubuntu Breezy to E: which is not a primary partition but a logical drive in an extended partition? Or would I have to delete the entire extended partition first (D: and E: drives) in order to create a new primary partition? I'd rather avoid the latter.

I am also concerned that installing Grub on the MBR in the WinXP partition will prevent further access to the hidden partition via the AccessIBM key. How can I avoid that?

I'd be interested in hearing from anyone with a similar configuration please.

---

### Post by justask on 2006-01-18
Seeing as there are no responses, let me rephrase the main question.

I have a disk partitioned with two primary drives I do not wish to touch, and an extended partition containing two logical drives ( D: and E: ). I want to keep D: intact and use E: for the Ubuntu install.

How should I proceed? Can I use the installer to shrink the partition leaving just D: and use the resulting free space for the install?

Thanks

---

### Post by Herman on 2006-01-19
justask, you asked,
>  Is it possible to install Ubuntu Breezy to E: which is not a primary partition but a logical drive in an extended partition Yes, you can do that, I install Ubuntu and other Linuxes on logical partitions very often. It doesn't seem to matter much as far as I can tell. Using logical partitions will make the install simpler.

Also, I noticed that you have an ntfs file system in Windows, so if you want, (generally recommended), you should be making yourself a separate fat32 partition to use for files you need both operating systems to be able to 'read' and 'write' to. (Ubunu can copy from ntfs, but it is dangerous to paste or 'write' to an ntfs filesystem from linux, fat32 is okay). 
You can use the traditional Ubuntu partitioner on the install disk to do this during your install, [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm"), but your install will be a little different from the one in the example in the link because you already have some extra partitions made.
An easier way to do your partitioning is to use the new GParted livecd-0.1, see my second signature link, bottom right of this post for where to download a Gparted livecd-0.1 .iso to burn to a CD. I highly recommend GParted livecd-0.1. (Some other linux partitioner of your choice will do, but the use of any non-linux partitioner is not recommended).
Delete whichever partition you choose (your 12.0 GB 'E' in your case), and make some of it into a fat32 logical. See my second signature link, bottom right of this post for where to download a Gparted .iso to burn to a CD.

Then when you run the Ubuntu install CD you can just select the remaining area (free space) you want to install Ubuntu on an let the Ubuntu installer 'automatically partition the free space, that will be the easiest.

Edit:  a better idea might be to make some of your  'D' drive 20 GB logical data ntfs into FAT32 instead.

---

### Post by Herman on 2006-01-19
> I am also concerned that installing Grub on the MBR in the WinXP partition will prevent further access to the hidden partition via the AccessIBM key. How can I avoid that?
 
You can install GRUB to a formatted floppy disk, when the installer asks you for permission to install GRUB to MBR later in the install, choose 'No', and you will be given the chance to install GRUB somewhere else. There will be instructions there for you to read, and I think you need to type /dev/fd0 on the line if I remember correctly. Installing GRUB on a floppy will be the simplest plan.

Another bootloader that is excellent if you want to leave your MBR alone is GAG. One advantage of a GAG boot floppy is it can more easily be reproduced and/or duplicated in case your floppy disk becomes corrupted or has coffee spilled on it or gets lost. (I have a puppy that destroys all kinds of things).
You can download a copy of GAG bootloader and make a GAG boot floppy for yourself, for more info on that, [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")
GAG boots Windows without much trouble, but you need to do something different during your Ubuntu install for it to boot Ubuntu. If you use the standard ext3 file system for Ubuntu, you can choose 'Go Back' when the installer asks for your permission to install GRUB to MBR. This will take you to the Ubuntu Installer Main Menu, and you can go down one line and install Lilo to your new Ubuntu partition.
If you choose to use the reiserfs file system for Ubuntu, Lilo doesn't always go on rieserfs. It doesn't work for me in some computers anyway. If you decide to use reiserfs, you may need to make a seperate ext2 or ext3 /boot partition to install GRUB in. (I made one 70mb and it was okay). Then GAG will boot Ubuntu plus any other operating system you like. 
(Actually, the computer I am using now has reiserfs with both GRUB and Lilo installed, so I can boot lots of different ways).
Have a good look around on my first 'sig link' website on the bottom right of this post when you have time, it has some other info you might also find handy.
Good luck with it, I hope some of this will help, :D (Herman)

---

### Post by justask on 2006-01-19
Thanks Herman.  Your pages were most helpful. Just to clarify things, here's how my disk is currently partitioned. I used the sysrescuecd to create the partitions anyway so partitioning is not the problem:

/dev/hda1    ntfs     active   19.42GB  winxp
/dev/hda2    extended          32.00GB
 /dev/hda5    ntfs              20.00GB data i don't want to touch
 /dev/hda6    ntfs              12.00GB data that can be deleted
/dev/hda3    fat32              4.50GB  recovery partition i must keep

I want to install Ubuntu to hda6 but preserve all other partitions in a dual boot configuration. 

My understanding is that I can delete hda6 and then use the resulting freespace for the install. However hda2 is not a primary partition; when I delete hda6 won't the resulting freespace be still contained within the extended partition or will the extended partition be automatically shrunk to the size of hda5?

Do I understand you to be saying that that's alright? 

Thanks

---

### Post by lha on 2006-01-19
[QUOTE=justask]Thanks Herman.  Your pages were most helpful. Just to clarify things, here's how my disk is currently partitioned. I used the sysrescuecd to create the partitions anyway so partitioning is not the problem:

/dev/hda1    ntfs     active   19.42GB  winxp
/dev/hda2    extended          32.00GB
 /dev/hda5    ntfs              20.00GB data i don't want to touch
 /dev/hda6    ntfs              12.00GB data that can be deleted
/dev/hda3    fat32              4.50GB  recovery partition i must keep

I want to install Ubuntu to hda6 but preserve all other partitions in a dual boot configuration. 

My understanding is that I can delete hda6 and then use the resulting freespace for the install. However hda2 is not a primary partition; when I delete hda6 won't the resulting freespace be still contained within the extended partition or will the extended partition be automatically shrunk to the size of hda5?

Do I understand you to be saying that that's alright? 

Thanks[/QUOTE]

I have no experience on dual-booting with XP, but if its mbr works the same way as Win9x's, here's a nice way to dual-boot without floppies or modifications to mbr.

Delete hda6 and replace it with a primary partition. You might need to resize extended partition but shouldn't be a problem. Install linux on this new partition and be sure to install grub to the boot sector of this linux partition, not to mbr. Then use fdisk or cfdisk or whatever to make this new linux partition active. (Toggle the boot flag on for linux partition and off for Windows partition.) You can now use grub to boot windows and linux.

If XP's stage1 boot loader differs essentially from older MS boot loaders, your system boots to Windows. Then you can boot grub and linux by copying boot sector from linux's root partition to a file in Windows and modify boot.ini to have the option to boot linux from there. BootPart is a program that helps to do this.

---

### Post by Herman on 2006-01-19
> My understanding is that I can delete hda6 and then use the resulting freespace for the install. However hda2 is not a primary partition; when I delete hda6 won't the resulting freespace be still contained within the extended partition or will the extended partition be automatically shrunk to the size of hda5? I think that when you delete your hda6 logical 12.0 GB data partition the extended partition will probably remain the same size and will contian 12.0 GB of free space for you to make new partitions in for your Ubuntu install.
If it the extended partition does shrink when you remove the old data partition, it shouldn't be anything to worry about, your partitioner will automatically make the extended partition larger again when you create a new logical partition. As long as it's still adjioing the other logical partitions.
The way some people get in trouble is, they try to make a new logical partition somewhere on the other side of a primary partition from the other logicals, then it won't be a useable partition. But what you want to do sounds 'A okay'. I don't think you'll have any problem if you make all logical partitions.
It's good that you have 'System Rescue CD, that has GAG on it, so you can use GAG from that if you like.
Iha is also correct, you can get NTLoader to work for you by configuring boot.ini if you are clever enough, I have never tried that.
If you decide to apply iha's method, and create a primary , just make sure you create that at the end of the available space so it won't break your chain of logical partitions. Create any logical partitions at the beginning of the available space so they wil adjoin you existing logical one. The main thing is to keep all logical partitions 'contiguous'.  :D (Herman)

---

### Post by justask on 2006-01-20
Thanks. I'll shrink the 12gb logical partition to 2gb and format it as fat32 for the shared data, and then set the boundary of the extended partition at 22gb.(Having the smaller fat32 partition as a staging post for shared data is not only a good idea, it will help avoid having to shuffle drive letters around in Windows where I use lots of removeable media.)

I'll go for a primary partition in the remaining 10gb freespace for the install. Does 4gb for / and 6gb for /home sound like a good way to apportion the space. I've a gigabyte RAM so I don't think a swap is necessary or am I wrong?

As for the bootloader, I'll try the grub way.

Thanks for your patience

---

### Post by Herman on 2006-01-20
Oh-oh, a few points in your most recent post are worrying me, you said,
>  I've a gigabyte RAM so I don't think a swap is necessary or am I wrong? That's probably right, I have never tried it myself (not having any swap at all), it might be okay, but I have seen others recommend making at least a small swap file just to make sure. I don't know whether you need to or if it's just a superstition. I wish someone who has tried without any swap at all would comment on this and confirm whether or not for sure this is okay.
>  Does 4gb for / and 6gb for /home sound like a good way to apportion the space. Yes, that would be fine, if you want two partitions, a seperate / and /home, lots of people like that. Personally, I like to keep it all as one single partition, but that's a matter for personal choice. Your apportioning looks okay.
>  I'll go for a primary partition in the remaining 10gb freespace for the install. This is the part that has me worried. You are allowed one more primary partition. If you don't split it up further into seperate / and /home it will be okay. If you do divide it further into seperate / and /home, at least one of these wll need to be logical, and if you make one of them primary, it will need to be at the end, so as not to interrupt the continuity of your logical partitions. In that case it will be okay.

The rules on partitioning say (basically) we can have as many as four primary partitions or three primary plus one extended with logical partitions inside it. These logical partitions should be 'contiguous', (all together in one group when viewing the partitions in disk order).
:D (Herman)

---

### Post by lha on 2006-01-20
[QUOTE=justask]Thanks. I'll shrink the 12gb logical partition to 2gb and format it as fat32 for the shared data, and then set the boundary of the extended partition at 22gb.(Having the smaller fat32 partition as a staging post for shared data is not only a good idea, it will help avoid having to shuffle drive letters around in Windows where I use lots of removeable media.)

I'll go for a primary partition in the remaining 10gb freespace for the install. Does 4gb for / and 6gb for /home sound like a good way to apportion the space. I've a gigabyte RAM so I don't think a swap is necessary or am I wrong?

As for the bootloader, I'll try the grub way.

Thanks for your patience[/QUOTE]

My system uses ~2GB of / so 4GB sounds ok. I recommend you to have swap, even though you have lots of ram. If you run out of memory, some of your processes will get terminated and you may lose data.  If you don't want to create a dedicated partition, you can make a [swapfile.]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") I've heard it has a bit lower performance than dedicated swap partition, but with your ram it shouldn't be a problem. (My system has only 512MB and I have needed swap only once.) A swapfile has its own pros. For example, if you need space on partition where swapfile is, you can make a new swapfile somewhere else and remove old swapfile.

---

### Post by justask on 2006-01-23
[quote=Iha]
     Delete hda6 and replace it with a primary partition. You might need to resize extended partition but shouldn't be a problem. 
[/quote]

I want to go with what you suggest here. However, rather than delete hda6, it will be shrunk as a smaller fat32 partition. Having done some experimenting with qtparted, I can see that resizing the extended partition will not be a problem and I will end up with 10gb of unpartitioned freespace. 

> 
    Install linux on this new partition and be sure to install grub to the boot sector of this linux partition, not to mbr. Then use fdisk or cfdisk or whatever to make this new linux partition active. (Toggle the boot flag on for linux partition and off for Windows partition.) You can now use grub to boot windows and linux.


I take it that I can just ask the installer to automatically partition the freespace but this new linux partition (and its boot sector where grub will go) will end up near the end of the disk. Is that ok?

Also how exactly do I use fdisk (or cfdisk) to set the new partition active?

Thanks again for your patience.

---

### Post by lha on 2006-01-23
[QUOTE=justask]I want to go with what you suggest here. However, rather than delete hda6, it will be shrunk as a smaller fat32 partition. Having done some experimenting with qtparted, I can see that resizing the extended partition will not be a problem and I will end up with 10gb of unpartitioned freespace.

I take it that I can just ask the installer to automatically partition the freespace but this new linux partition (and its boot sector where grub will go) will end up near the end of the disk. Is that ok?[/QUOTE]

As you have not posted output of "sudo fdisk -l", I am not 100% sure of your current partition layout. (Windows-like info leaves room for guesses.) If you are set up like this

hda1  NTFS   C:
hda2  extended
|->hda5 NTFS   D:
|->hda6 NTFS   E:
hda3   hidden recovery

your plan looks good. But, because you already have 3 primary partitions, one being extended, installer may have difficulties if asked to do automatical partitioning.

You can use qtparted to do the partitioning. Again, I recommend to make a swap partition. So before shrinking extended partition, make a swap partition (and any additional partitions if you wish, don't need to if you don't want). If you are brave enough to go without swap or want to use a swap file, you are on the right track.

When installer asks if it is okay to install grub to mbr and you say no, you are asked where you want to install grub. Be sure to remember the partition where you installed Ubuntu.

[QUOTE=justask]Also how exactly do I use fdisk (or cfdisk) to set the new partition active?

Thanks again for your patience.[/QUOTE]

You can use qtparted to do that, too. I have had troubles with qtparted (and almost every other partitioner, too), but not with cfdisk and that's why I talk about it. All in all, you are familiar with qtparted and therefore it may be a good choice for you. If you can't find out how to set a partition bootable/active with qtparted just ask and I'll tell how to use cfdisk.

---

### Post by justask on 2006-01-27
Did the installation successfully but the only way I could get grub to work was to install it to the MBR; installing it in the ubuntu partition resulted in a missing os error. 

However, having the mbr modified has had the effect of making it impossible to boot into the IBM rescue partition. 

The problem (and hopefully, the solution) is as described by Andreas in this thread [here]("http://sharadware.com/2005/07/11/suse-linux-winxp-access-ibm-on-the-thinkpad-t43/#comment-165")

Thanks Herman and Iha for all the help.

---

