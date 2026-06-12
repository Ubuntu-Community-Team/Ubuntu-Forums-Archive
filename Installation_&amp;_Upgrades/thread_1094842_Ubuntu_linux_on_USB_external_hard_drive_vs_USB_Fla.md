---
title: "Ubuntu linux on USB external hard drive vs USB Flash pen drive"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by IsmailBhai on 2009-03-13
I was wondering if anyone can be kind enough to explain the difference between the 2 processes.  I know there is a difference between booting from a flash drive versus rotating platters, but don't know exactly what.

---

### Post by martrn on 2009-03-13
> **IsmailBhai said:**
> I was wondering if anyone can [..] difference between the 2 processes [..] difference between booting from a flash drive versus rotating platters, [..] .

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
https://help.ubuntu.com/community/Installation/FromUSBStick[/URL]

A file system on a USB hard drive, such as one with a rotating disk with platters will have one type of controller on it where it can be formatted and read and written two using the native file system of the host operating system.  Quite ofter the controllers on a rotating spindle hard disk will be well supported by most operating systems.

A pen drive from a USB stick will usually be formatted with FAT32 or FAT16 file system, more often than not the ubiquity of this file system allows the drive to be accessed on virtually any host device with USB support. I will have a small control chip on board the pen drive and most sectors are 512 bytes long, for compatibility with hard drives, and first sector can contain a Master Boot Record and a partition table. theoretically most USB flash units can be partitioned as hard drives, but the controller chips are not brilliant.

Aside from that a pen drive will last a certain about of read/write cycles where you should be able to thrash a hard drive with rotating platters for years, without any problems.  It would last longer and wouldn't think you could get anywhere near the amount of wear and tear on flash pen drives, although things do move gradually on.

Some motherboards will support booting from some pen drives if they are formatted with FAT16 but more modern day motherboards (today) support both booting with FAT16 or any hard drive with a partition table and MBR (master boot record) in the first 512 Bytes of the disk / pen drive.

Source :
From memory and && 
[http://en.wikipedia.org/wiki/USB_flash_drive]("http://en.wikipedia.org/wiki/USB_flash_drive")

---

### Post by Herman on 2009-03-13
When you have a mechanical hard disk drive, the safest place for it is securely mounted inside a desktop computer.
Hard disc drives are vulnerable to damage if they are roughly handled, especially if they are accidentally dropped or banged around too much, even if they aren't spinning at the time. When the platters are spinning, they are even more easily damaged.
Nevertheless, external USB hard disk drives are popular, because of the larger file storage capacity they allow, and the fact that they can easily be used to transfer files from one computer to another. Most of the time, people handle external hard drives carefully and they last quite a while. Other times, accidents happen and well... the rest depends on your luck.
I have Ubuntu Rescue Remix in an external hard disc drive because I like the larger capacity for space for recovering files to.

USB flash memory sticks currently don't have anywhere close to the storage capacity of hard disk drives, and they're currently much more expensive per GB. 
However, they're quite robust. You can drop them from a fair height and chances are they'll not be harmed at all, especially if you have one with a good case.
Flash memory has a bad name for wearing out because not so long ago the life expectancy of flash memory was about 10000 writes per cell. Most flash memory sticks that ordinary people could afford then were very small too, so there weren't many cells to share the wear.
Now flash memory has more like a million writes per cell and flash memory sticks of 8 GB are common. Up to 64 GB sticks are available. The flash memory controllers have wear levelling features and they spread the wear evenly across all the cells.
Flash memory is quick to read from but it's generally slow to write to because of the way the wear levelling works. If you just want to write to one sector, it needs to erase a whole cell and write it again somewhere else. 
The write speed for small files can be improved by using the reiser file system if you use Linux. You can also use GRUB as a boot loader if you like. There's no real difference between booting in a USB flash memory device compared with booting a USB hard disc as far as the user or the operating system are concerned. I have several USB flash memory sticks with Ubuntu installed in reiserfs in them booting with GRUB.
More laptops are coming onto the market without hard drives but with flash memory instead, (quieter, use less power, less likely to be damaged from dropping). I have an EeePC myself and I think it's great. 
SSD drives are coming down in price and we may see SSDs in external USB cases around more. When USB3 becomes available, I imagine people will be installing Ubuntu in external USB3 SSD drives and it will be a good thing for Linux and open source. Ubuntu will become much. much, much more popular than it is already.

That's only my guesswork and opinions, take it with a grain of salt if you like, but see if I'm right. 
Regards, Herman :D

---

### Post by IsmailBhai on 2009-03-13
thanks to both of you for taking the time to reply. I still don't understand quite fully why we have to use liveusb or Unetbootin on a Flash drive even though the BIOS detects the drive, whereas you don't do this on an external drive.

---

### Post by Whorehay on 2009-03-13
From [**_[COLOR="Red"]UNetbootin[/COLOR]_**]("http://unetbootin.sourceforge.net/")'s website:
> UNetbootin allows you to create bootable Live USB drives for a variety of Linux distributions from Windows or Linux, without requiring you to burn a CD.

UNetbootin doesn't really install the distro on your USB flash pen drive, it just allows you to boot from it or use it as a [**_Live CD_**]("http://en.wikipedia.org/wiki/Live_CD").   If you just copied the .iso file on your pen drive/hard drive nothing would happen.

---

### Post by Herman on 2009-03-13
Yes, that's right.

The good thing about the Live CD type of installation is that you will have the ability use the to installer to install Ubuntu in another disk, just as if you were running from a Live CD, but it's in a USB stick. Some people want that because they might need to use it for installing Ubuntu in a computer that does not have a reliable CD drive, or because they want to use the Live CD to show Ubuntu off, and they want faster performance than a real CD in a CD drive can deliver.
Also, there are no writes to disc in a Live CD, so if you are afraid that your flash memory will wear out quickly, you will have the longest life from the flash this way.

You can also install Ubuntu as a Live CD with 'persistence', which means you can install software and it will save your settings and files almost like a real hard disk type of installation does.

In my opinion it is quite alright to just install Ubuntu in a USB flash memory stick the same way we use to install Ubuntu in any other kind of disk, that's the way I do it myself. There will be no 'install' icon on the desktop, and you can't use it to install Ubuntu somewhere else, but then I have a 'real' installation and all software and programs will work normally. I found that there are some programs I want to use from the flash memory that don't work properly from the 'persistence' type of installation, such as AVG virus scanner, for helping Windows users diagnose problems. So far, I haven't had any flash memory wear out yet.
If one ever does wear out, it's only about the price of a tank of gas now for an 8 GB USB flash memory stick anyway so I don't know what all the fuss is about. I will have had enough work done to more than pay for a new flash memory stick by the time one wears out. (If that ever really happens).

Regards, Herman :)

---

### Post by martrn on 2009-03-13
Installing ubuntu to a flash drive you will have a 'real' file system on your flash pen drive, just as a regular install but to a pen flash drive rather than a hard disk.  There will be different performance than on a hard drive installation, and you may notice quicker read/writes than on a hard disk with platters (less time to seek etc).

If you have a pen drive and you use it as a normal type installation, take backups of your pen drive to an alternative media for important files, as you would take backups of a hard drive installation.  

Flash drives that have 'bad' sectors or will mark the sectors as 'bad' and the file system will then not write to the 'bad' sectors.  Some people continue using flash drives with no problems with the 'bad' sectors.

If you notice a considerable slowdown on your pen drive, just get a new one, and copy or restore it from your backup or other pen drive.  Pen drives are pretty much a good medium between a permanent hard disk and a rewritable CD or a zip drive.

---

### Post by rdotex on 2009-03-14
I want to install Ubuntu 8.04 to an 8 GB usb stick.  How should I partition it for best results?

---

### Post by martrn on 2009-03-14
> **rdotex said:**
> I want to install Ubuntu 8.04 to an 8 GB usb stick.  How should I partition it for best results?

Install lilo, don't exept it to boot from every computer and partition the disk with the REISER file system.  Don't install grub use lilo.

---

### Post by ve4cib on 2009-03-14
> **martrn said:**
> Install lilo, don't exept it to boot from every computer and partition the disk with the REISER file system.  Don't install grub use lilo.

I installed Ubuntu onto a 2GB stick formatted to a single EXT3 partition, and am using GRUB.  So far every computer I've tried it with (that had bios support for booting from a USB device) has booted off of it just fine.

Any particular reason you're advocating lilo and ReiserFS?

---

### Post by martrn on 2009-03-14
> **ve4cib said:**
> Any particular reason you're advocating lilo and ReiserFS?

I only advocate ReiserFS for speed, its a bit more efficient with space, (like when using a pen drive with less space than on a hd) it used different storage and retrieval algorithms (in the kernel).  I would still advocate ReiserFS if you wish partition a pen drive "to achieve best results" (speed and efficiency where space is a consideration.).

I can't boot to a pen drive in [some] computer systems where others I can.  I can Boot into a floppy with lilo on it and it continues booting from the pen drive, Something I have never managed to do from grub.  Grub is more for stable booting system (IMHO).

-----
I could be wrong - To err is human.

---

### Post by Herman on 2009-03-14
I would choose manual partitioning when you get to step 4 of 7 in the installation process and create one partition for / (root).
Most people leave a little space after it and create a swap area, say about 512 mb to 1 GB. If you want to keep things simple, just create a small swap area.

[I]You'll need a larger swap area if you want to 'hibernate' your operating system rather than shutting it down, but I don't think you'll have room for a swap area that large in an 8GB USB, so unless you're really determined to hibernate at the expense of disc space, then just a small swap area will do.
[/I]
Many computers now have so much RAM that a swap area is rarely used anymore. In a USB installation you want to use your disc area as efficiently as you can.
A better suggestion if you have time are willing to do a little work is to not create any swap area at all. 
You can get Ubuntu to use a swap file instead, with a little edit in your /etc/fstab file after Ubuntu is installed, plus a few easy commands, [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")
If you do that, then you can quite easily resize the swap file if you decide later that you'd like it to be a little larger or smaller. (You can resize a swap area and partition too, but I think it's more work).

You can set the swappiness to zero after Ubuntu is installed to increase the performance (speed) and possibly save a little flash memory wear, (if you're afraid of that).
Swappiness in Ubuntu can be tuned by editing /etc/sysctl.conf, see [https://help.ubuntu.com/community/Sw...ness'']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27")

If you use the reiser file system, you can also edit your /etc/fstab file after Ubuntu is up and running, to turn off file system journalling. Refer to this link, [nolog]("http://ubuntuforums.org/showpost.php?p=5882924&postcount=69").
That is also supposed to reduce flash memory wear and improve performance by reducing disc writes.
I'm mainly interested in any speed improvement that I can gain rather than reducing wear, but since they both go hand in hand, then why not?.

UPDATE: The new ext4 file system is supposed to be even faster than reiserfs, it will be an option in the soon-to-be-released Jaunty Jackalope.

If you want to use GRUB, you can install with either the 'Alternate' CD or 'Desktop' (Live) CD. 
In the 'Desktop' Live/Install CD you do that in step 7 of 7 by pressing the 'advanced' button and selecting which partition (boot sector) or which hard disk (MBR) for GRUB to be installed in, and select your USB's MBR. 
If you are using the 'Alternate CD' to install with, you click '[No]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")' when it asks you if it can install GRUB to MBR in the first hard disk, and specify your USB's MBR.
Don't go to sleep during the installation and forget or GRUB will automatically be installed in your first hard disk's MBR.

---

### Post by Herman on 2009-03-14
If you want to install LiLo instead of GRUB as martrn suggested, you can only use the 'Alternate' CD to do that. choose <Go Back> when it asks you if it can install GRUB to MBR in the first hard disk, and  you will be placed in the 'Ubuntu Installer Main Menu', where you can scroll down just one line and install Lilo bootloader instead. 

If you do decide to use LiLo, you need to be aware that you'll find it necessary to revert  your /etc/fstab file from file system uuid descriptions to the old style of file system entries based on 'dev/sdx,y' type notation, see [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig").
You'll also need to remember to run Liloconfig again after every kernel update.

Apart from those two considerations, I don't think it really matters if you want to use LiLo or GRUB for booting Ubuntu Hardy Heron 8.04 or earlier versions of Ubuntu in a USB.

---

### Post by Herman on 2009-03-14
For Ubuntu Intrepid Ibex and later versions of Ubuntu, I think the improvements in GRUB are ideal for USB booting, so I would highly recommend GRUB if you're installing one of the latest versions of Ubuntu in a USB device, especially if you're going to expect your USB to boot in more than just one computer.

Most BIOSes like to number SATA drives first, followed by PATA (IDE) drives, and list any USB devices last. 
Other BIOSes list the drives belonging to the different interfaces in a different order. Some list PATA drives before IDE, and others even list USB devices first.
In addition to that, you may be trying to boot it in computers with various numbers of hard disk drives. Some computers might only have one hard disk drive, others may have quite a number of hard drives.

Ubuntu Intrepid Ibex and later feature the uuid command in the latest GRUB.
With UUID booting, you can boot a USB no matter what number the BIOS wants to give the USB drive.

No matter how many other USB drives and other kinds of hard drive you might have plugged in to a computer at the same time, with GRUB's new uuid command, GRUB will always be able to find the right root and boot partition and boot your USB for you. :D

---

### Post by rdotex on 2009-03-14
Herman:

When you say, "I would choose manual partitioning when you get to step 4 of 7 in the installation process and create one partition for / (root)", do I understand you correctly that you mean you would create_*just one*_ partition (= "/") and no others?(edited to re-phrase more clearly!)

---

### Post by Herman on 2009-03-14
Yes, just one partition.

It's always a waste of disk space dividing up any disk into multiple partitions.
If we divide an installation up into more than one partition, we are setting boundaries and limitations on ourselves for no good reason. It's necessary to make each partition much larger than it needs to be to allow for an unknown amount of future growth.

I always prefer a single partition install over the separate /home and / type of installations, if that's what you're asking about, even in a hard disk where I have plenty of room. In a USB flash memory stick, we don't typically have a lot of spare disc space to waste.

If you have one partition, the directories inside it are always exactly the size they need to be at all times, and we have a trouble free installation.
Want to install some large files? No problem, the home directory will resize itself accordingly in the background without the user having to do anything.
Want to install some extra software? No problem, the operating system directories will resize themselves to accommodate it. 
No resizing with a hard disk partitioning program is necessary.
No head scratching and nail biting decisions need to be made during installation over how large to make the / partition and /home. 
No regrets in the future from a bad decision at installation time.

There's actually very little advantage in having a separate /home when you think it over. We really should be keeping a backup of at least all of our most important files on some other media instead. It only takes a few minutes to make a complete backup of a home directory or to restore one from a backup. Therefore, I think that a separate /home is just a waste of disc space. 

I don't even like having a separate swap area if it's only for one operating system.
Most of the time in internal hard discs I multi boot though, so it makes sense to have one swap area that can be shared between all OSes.
With the amount or RAM in most computers these days, the swap area won't be used very much, especially if we turn swappiness down to zero. 
If we use the USB flash memory in an older computer with somewhere between 256 and 512 MB of RAM, the swap area will be needed. When we have a swap file instead of a partitioned swap area, we can resize the file according to our needs. 
That can save quite a lot of disc space in an 8GB flash memory. 

...but those are just my personal opinions, there are many who would argue the opposite. Feel free to use your own ideas and judgement.  :D

---

### Post by rdotex on 2009-03-14
OK.  Thanks Herman.  That's just the kind of info I needed.

I really appreciate it.  Will let you know how the installation goes tomorrow.

---

### Post by rdotex on 2009-03-20
Sorry for the long delay, but other things had priority...darn it!

It seems that the install went OK, though it took quite a while.  But only one of my computers will boot from the USB.  Just now got to try it on that one and all I get is a "grub>" prompt and, sadly, I don't know what to do next!  Please help!

---

### Post by Herman on 2009-03-20
If you have a GRUB>_ prompt, that means your /boot/grub/stage2 file is working okay and you can use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
That usually happens if there's no menu.lst file or if the menu.lst file has been renamed, or if the stage2 of GRUB can't find it.
You should be able to boot your Ubuntu Live CD and mount your USB, (if it doesn't mount by itself), and take a look around in your USB's /boot/grub directory for a menu.lst file.

Sometimes, the /boot/grub/menu.lst file is there but stage2 can't find it because of a file system problem.
You can fix that by unmounting your USB from your Live CD and opening GParted. 
'System'-->'Administraion'-->'Partition Editor'.
Right-click on your USB file system and click 'Check', then 'Apply', and 'Apply' again.
GParted will run a file system check in that partition for you.

Never just rip your USB out of the USB port whenever you finish using it.
Always do it the polite (and gentle) way by right-clicking on the icon for it on your desktop and clicking 'Unmount Volume', and wait a few seconds before unplugging your USB drive. That givs the Linux kernel time to finish off updating any information it hasn't writeen yet to your USB's file system metadata. 
File system 'Metadata' is data about data', or in other words, where your file system keeps it's record of where it has left your files. (So it can find them again for you or your programs - such as GRUB and other programs).  

I'm not sure if that's your problem or not, I'm only guessing. 

Many Windows users who I show Ubuntu to think that seems like a strange chore, and claim it's not necessary in Windows. Many are surprised to learn that they are actually supposed to do the same thing in Windows too. In Windows it's harder, and not so many people know about it.  I think it's in 'My Computer' somewhere, and right-click on the USB drive and dismount it, or something like that, I can't remember exactly.  I'd need to boot Windows to check.

---

### Post by Herman on 2009-03-20
> But only one of my computers will boot from the USB
Not all computers can boot from USB. It depends on what kind of BIOS the computer has.
Even some new computers can't boot a USB drive. My newest one can't, (or at least I haven't discovered yet how to get it to do so).

If you think there might be a BIOS setting you've missed, a good test is to try to boot your USB drive in the computer that can't normally boot a USB from Super Grub Disk or some other GRUB. If you can boot it from another GRUB then probably there's a BIOS option you didn't find, and you should keep looking. Otherwise, you might have to give up and use your USB Ubuntu in another computer that can boot a USB drive. It's something to check before you buy a new computer next time or before you upgrade your computer with a new motherboard. :)

---

### Post by TrueLugia121 on 2009-04-10
heh yeah it is easy to install Linux on the Master Boot Record of a USB External Hard Drive. got Fedora Core 9 on my 118GB Seagate FreeAgent Go and am just about to set up to install Ubuntu Studio 8.10 on my Western Digital 250GB USB External Hard Drive.

what i don't understand is that how can i take like for example my Fedore Core 9 USB External Hard Drive, since it says it's installed onto my laptop (HP Pavillion), and take it here to do some internet package management? like i want to take that operating system to my father's place since he's the only one with internet connection do some packaging on it and take it back home with me. can anyone tell me if that's possible?

EDIT: sorry if i've revived an old thread.

---

