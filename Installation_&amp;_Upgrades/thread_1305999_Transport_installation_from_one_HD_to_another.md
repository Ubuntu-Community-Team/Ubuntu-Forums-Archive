---
title: "Transport installation from one HD to another"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Aero-Z on 2009-10-30
Hello,

I'd like to swap my current HD out for a bigger one. The problem is that I would like to skip the reinstallation and configuration of new install.
Is it possible to transport my Ubuntu from my current HD to another one?

Thanks.

---

### Post by Herman on 2009-10-30
The easiest way to do that would be to use a 'dd' command.
You should make a backup of your files first if you haven't recently done so already.

Plug both of the hard drives into the computer at the same time.
Boot from a Live CD.
Open a terminal in your Live CD and first make sure you know which disk is the empty one and which one is the one that contains the operating system and files.
Take a good look with GParted partition editor and/or use 'sudo blkid'.

I normally take the time to create new partitions in the new disk which are equal or larger than the ones in the old disk.

If /dev/sda2 is the partition which contains Ubuntu, and /dev/sdb2 is the partition in the empty hard disk,
```
dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror
```Be careful with the dd command and make sure you copy the full disk to the empty one. If you make a mistake and do it the other way around and accidentally copy the empty disk to the full disc you will erase the operating system, so check twice before running your command. As long as you use it correctly, the dd command is your friend.
Here's a link with more about the dd command,[Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

You'll also need to install your boot loader to MBR in the new disk.
**[]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")**

---

### Post by Aero-Z on 2009-11-02
Thanks. The problem is that I want to change my laptop's HD so connecting both at the same time is kind of complicated :P
Also how can I install the bootloader to MBR in the new disk?

---

### Post by Mustard on 2009-11-02
I'm just going on faded memory of a very old thread, but it might be possible you could just transfer all files (via a compressed file) directly from one drive to another, assuming you had a similar partition setup already and an identical filesystem. Then install grub?  

Dont quote me on this. :)  It comes with no warranty.

I'd be curious about the outcome myself.

I guess it would come down to whether your new hard drive would play nicely with the old operating system....

---

### Post by Herman on 2009-11-02
> Thanks. The problem is that I want to change my laptop's HD so connecting both at the same time is kind of complicated  :-k Oh, I see, ... that does seem like it could be quite a challenge.

What other resources do you have available?
Maybe you have a large USB disk of some kind? 
Or some DVDs? 
Do you have any freinds who have a desktop computer you can use that has some spare IDE cables or SATA cables?
An external USB hard drive caddy?

Partimage is a program for cloning hard disk partitions and I have many times used it to clone entire operating systems. 
Partimage makes the partition into a series of compressed files, you can sset the size you want. That way you can make the files the right size to fit on DVDs or maybe even a number of CDs.
Clonezilla is another program I remember trying out that is for cloning disk partiitons. I haven't practiced with that one enough to be able to advise you on what it can or cannot do. You might be able to find out.

Parted Magic Live CD is an excellent Linux distro that I know of which boots in the CD drive and loads itslef into the RAM and runs in the RAM. Once it has booted, it will still keep running after it ejects the CD, leaving your CD/DVD drive free for making data CDs or backups.
Parted Magic contains Partimage and Clonezilla and a lot of other useful programs.

Parted Magic's main program is GParted. 
Depending on the size of your hard disk and the amount of free space you have left in your operating system, you might be able to resize your partition with GParted to around half of the disk size. If you create another partition you'll be able to have Partimage or clonezilla copy the files it makes from your old partition to that one and then you can burn them to disc later.
There may even be a way to burn them directly to disc ffom Partimage or clonezilla, I'm not sure but it would be worth looking into. If you can get Partimage or Clonezilla to work that way you won't need to shrink the partition first and you won't need to make another partition. You'll just need to keep feeding CDs or DVDs in and out.

---

### Post by Herman on 2009-11-02
Links:

[Parted Magic]("http://partedmagic.com/")

[Partimage]("http://www.partimage.org/Main_Page")

[Clonezilla]("http://clonezilla.org/")

aysiu's Partimage tutorial, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")
   **NOTE: **Use your *spacebar* on your keyboard to move the cursor in Partimage.

---

### Post by Aero-Z on 2009-11-02
Thanks. I'll check them out. I might be able to hook the new HD with a special adapter into USB port.

---

### Post by Herman on 2009-11-02
Reinstalling the boot loader.

If you have an older version of Ubuntu you probably have GNU GRUB 0.97, ('Legacy' GRUB, which is the 'old' GRUB). If that's true you can use Super Grub Disk to restore GRUB.
Super Grub Disk is one of the options you'll see when Parted Magic LiveCD is booting up, scroll down to the bottom of the boot menu.
One problem I ran into just the other day though, was the version of Super Grub Disk in Parted Magic doesn't know how to read my ext4 file systems, so it won't work if you have the latest Ubuntu.

If you have the latest Ubuntu,  Karmic Koala, it has GRUB_II and you should use the 'sudo mkrescue', to make a GRUB_II .iso file to burn to CD before you remove the old hard disk. [How to make a bootable GRUB2 CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM") - with grub-mkrescue.
Then you should be able to boot your operating system in the new disk with that.
Once your operating system has booted, run 'sudo grub-install /dev/sda'.
****

---

### Post by Herman on 2009-11-02
> I might be able to hook the new HD with a special adapter into USB port.If you have something like that it will make your job a lot easier.

I just received a new one in the mail this evening myself, direct from Hong Kong, it was only a couple of dollars, through ebay. It's a USB external SATA disk enclosure for 2.5" (laptop size) drives. I only had the IDE kind before. USB drives or drive enclosures are very handy. :D

---

### Post by Aero-Z on 2009-11-02
> **Herman said:**
> If you have something like that it will make your job a lot easier.

I just received a new one in the mail this evening myself, direct from Hong Kong, it was only a couple of dollars, through ebay. It's a USB external SATA disk enclosure for 2.5" (laptop size) drives. I only had the IDE kind before. USB drives or drive enclosures are very handy. :D
I checked Clonezilla out. Seems like that's the one I'm going to use. Look at the video - [http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla]("http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla")
If I use that utility then do I still need to reinstall GRUB?
PS. Yes, I have 9.10 :)

---

### Post by Herman on 2009-11-02
Yes, you'll still need to re-install GRUB.

I'm not sure, with Clonezilla you might not need to because I think it might be possible to clone the entire disk with Clonezilla. 
Try it and see if it will boot.
If it doesn't, then you should be able to fix it by re-installing GRUB.

I normally use Partimage mainly because I'm used to it, and I always need to re-install GRUB.
It's a good idea to re-install GRUB anyway, it won't do any harm and might do some good.

Since you have Ubuntu 9.10 you'll probably have GRUB_II.
It would be best to make a GRUB_II  CD for yourself with grub-mkrescue.
That should boot Ubuntu for you in your new hard disk, then you should be able to run grub-install from within the running operating system, that's the best and easiest way.

You should be able to install GRUB from a Ubuntu Live CD too if you need to. The quickest and easiest way would be, [How To Re-install GRUB from Live CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD").

You also might want to give your file system a check by right-clicking on it in GParted and (providing it is unmounted), click 'check', from the right-click menu.

---

