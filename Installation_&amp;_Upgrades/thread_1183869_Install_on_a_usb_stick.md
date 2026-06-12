---
title: "Install on a usb stick"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by LoonyPhoenix on 2009-06-10
Can anyone tell me what would happen if I installed Ubuntu 9.04 on a usb stick? I mean directly, not through Unetbootin or LiveUSB creator. Is it safe for the system? Would it be a LiveUSB (i.e., would it work on other machines, not the one I installed it from)? Would it take more/less space, would it be fater/slower than traditional LiveUSB? Other advantages/disadvantages over a LiveUSB install?

Thanks in advance.

---

### Post by Mighty_Joe on 2009-06-11
I run Ubuntu from a USB flash drive.  I take my work laptop home, but when I'm doing things unrelated to work, I don't want to run the risk of polluting my work environment.
It runs much faster than a Live CD.  The Live CD is a compressed live file system which has to be swapped into memory in order to run.  A full install to a USB drive doesn't have to be uncompressed, so it is faster.
My USB install has worked on every system I've used it on.  In just the last few minutes, I've booted up an HP 8510p laptop and an HP dc7100 desktop.  No problem.  Boots up quick, too.
A Live CD install can fit on a 1Gb USB drive.  A full install will take over 2Gb.
I *believe *that one cannot upgrade the kernel on the Live CD install because the "regular" Ubuntu kernel doesn't have squashfs, which is what does the compression mentioned above (could be wrong, can't find cite). Another problem with updates is that updated files can't replace the original files in the compressed Live CD Image, so you end up with the updates taking up valuable real estate in your persistent partition.
One problem with all flash memory is that it will eventually [wear out]("http://en.wikipedia.org/wiki/Flash_memory#Memory_wear").  I store all my important files on a NAS device and I purchased a flash drive with a lifetime replacement warranty (just in case!) ;)
I used the instructions [here]("http://beastie.cs.ua.edu/cs150/usb-install.html") to install and [here]("http://beastie.cs.ua.edu/cs150/configuration.html") to configure my flash install for (hopefully) the best performance and least wear-and-tear.

---

### Post by LoonyPhoenix on 2009-06-11
Thanks for the reply!

I tried to install Ubuntu 9.04 (well, Linux Mint 7, but it shouldn't matter, right?) on my usb stick, but it refuses to boot. The GRUB showed up fine, but nothing further. Said something like "can't boot from that device". So I edited the boot entry (changed hd(2,1) to hd(0,1) and /sdc2 to /sda2" and then I saw a flicker of the splash screen, but after that the system stopped at a command prompt with (initramfs) in the beginning and a mistake like "can't mount /dev /root/dev because the file doesn't exist" and "can't find init in /sbin/init, specify it in the init= boot option".

I browsed a bit around the filesystem, and it doesn't seem like the one on the usb drive. It doesn't have /home, for one. However, it does have /dev, /bin, /sbin and some others. So I lsed /dev and saw that there is no device to correspond to the usb drive; I could only see the machine's hard drive. Seems like just after loading the kernel the system stops seeing usb drives, including the one it should be booting from.

I'm very confused why it doesn't work for me. Usual LiveUSBs boot just fine on the laptop.

---

### Post by Herman on 2009-06-11
Usually, we can easily install Ubuntu (or Mint) to a USB flash memory stick in the usual manner, the same way as if we were installing to any hard disk drive.

I prefer the reiser file system for flash installations, it seems much faster in most kinds of flash memory. The new ext4 might be even better, I haven't tried it out enough yet to be sure, but I think ext4 is very good.
It's best to choose to install GRUB to the USB's master boot record and possibly the system's partition boot sector as well.

You might have some trouble with Mint's GRUB because Mint doesn't use the file system UUID booting method that Ubuntu's GRUB uses. That means every time you boot the USB stick in a different computer you'll have trouble because it'll be some other (hdx) number. You should be able to edit your /boot/grub/menu.lst with the UUID numbers like we use in Ubuntu and it should work, it's the same GRUB I think.  
In case you don't know what I'm talking about, here's a link about uuid numbers, [uuid]("http://members.iinet.net.au/%7Eherman546/p15.html#root")
You should be able to boot into [GRUB's Command Line Interface]("http://members.iinet.net/%7Eherman546/p15.html#cli") and use the uuid command to get a list of your UUID numbers, then add the right one for your Ubuntu USB installation to your /boot/grub/menu.lst file.

Unless you have other problems as well. Some computers can't boot a USB device, (even some new ones), and I have run into one brand of flash memory which doesn't seem to be suitable for this kind of use. Most flash memory seems to be okay.

---

### Post by LoonyPhoenix on 2009-06-12
Thank you very much! :) This was illuminating, and helped a lot. I wonder why Mint doen't use uuids like Ubuntu does.

By the way, I have the casper-rw file from my old LiveUSB intallation (backed it up in case something went wrong). Can I salvage something? I've done a lot of intalling and configuring on my old system and I don't want to lose it all.

Anyway, that aside, I'm very happy with the results.

Oh, and: I chose to use ext4 as the file system. I have a pretty fast flash drive and I'm not too worried about the wear (it has life warranty, whatever that means) - it's OCZ Rally2. Do I need any special tweaks (like, different mount options, etc.) to improve the performance a bit more?

---

### Post by Herman on 2009-06-12
> I wonder why Mint doen't use uuids like Ubuntu does.
I don't know. I got the impression they don't like the use of UUIDs in GRUB from some reading I did in their web forum a while back, I can't imagine why.  I think booting with UUID numbers is the best invention since sliced bread!
It will be particularly useful when USB3 comes in, and people will likely be installing Linux operating systems in USB SSD drives so they can carry their own operating systems around in their pockets, complete with all of their favorite files and settings.
I think USB3 will dramatically change the way we use computers in the future, and most likely in Linux's favor. Computers will be more like boxes that we plug our USB3 drive into, I imagine. USB3 will start to appear sometime soon. It will be a while before it gets to my neck of the woods though.
> I have a pretty fast flash drive and I'm not too worried about the wear (it has life warranty, whatever that means) - it's OCZ Rally2.:D Oh wow! I'm jealous! I'm a big fan of OCZ drives and I want one too! I really want an OCZ brand SSD drive! I'll get one sometime soon.
> Do I need any special tweaks (like, different mount options, etc.) to improve the performance a bit more? Not really, especially with a good quality brand of drive like OZC, but there are a few things that won't do any harm and may boost your speed a little. I'm out of time for now, I'll come back and elaborate later on . . .

---

### Post by LoonyPhoenix on 2009-06-12
> **Herman said:**
> :D Oh wow! I'm jealous! I'm a big fan of OCZ drives and I want one too! I really want an OCZ brand SSD drive! I'll get one sometime soon.
I think you misunderstood me; it's not an SSD that own, it's a plain 8 GB USB stick, the one that I'm booting from. Still, it's OCZ, and I know it should be good.

Anyway, thanks for all the help.

---

### Post by Herman on 2009-06-14
Well, a USB flash memory stick has flash memory inside it and so does an SSD drive.
The difference is, an SSD drive is bigger and faster. 
From what I understand of what I've read, an SSD drive has several pieces of flash all put together in one box. They're connected a kind of a RAID array, and that's the main reason an SSD drive is a lot faster than just a USB flash memory stick. The material the flash memory is made of is pretty much the same stuff as far as I know.

I'd buy a OCZ flash memory stick tomorrow if one was for sale in my town. The last time I googled for OCZ products it looked like they're hard to get in Australia. A few retailers advertised them, but thier web pages said they were out of stock. I think they put a big markup on them in this country too. I'm wondering if I can order from overseas.
In the meantime, I have to be content (or discontent) with inferior brands of USB flash memory sticks, whatever I can get my hands on.
What I really want someday is an OCZ SSD drive though like a vertex.

I have a few USB flash memory sticks and some of them have Ubuntu installed in them, but I don't use them full time so I don't see the need to take any special measures to make sure they don't wear out. Some of them are getting old already and I haven't had one fail yet.
I fixed a computer for an old lady who takes perfect care of it, so much that she's scared to even use it. It's getting old and obsolete but it's in mint condition. She doesn't even know how to do much with computers because she's afraid to try things. She's missing out on a lot of fun because she's being too careful.
I have a whole room full of old obsolete computer parts that nobody will ever want because they're all superceeded by newer, faster, smaller and more efficient technology.
SO, my idea is to just use things and accept the fact that they might wear out eventually and have as much fun as you can while you're doing it. Don't pay any attention to worry-worts or people who try to scare you about everything. Just do our work or have fun!
You have a good brand of flash memory, it will last you for a long time anyway.
I tune my flash memory installations for speed, not for long life.

I'm not sure how many GB your USB flash memory stick is, but my eeepc has a 4 GB SSD drive plus a 4 GB SSD card in it. I leave it on 24/7, but it doesn't do a lot of file system intense work. I use it mainly for Skype or for taking with me when I go somewhere.
I followed this how-to  [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")
I set my swappiness to 10,  [Performance tuning with 'swappiness']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27")
I'm using reiserfs with the options nolog,notial, relatime in /etc/fstab.
That's about all I can remember, I use a special eeepc kernel.

It may wear out someday, but in the meantime it's fast and it does everything I want and I'm betting it'll last plenty long enough for me to get my money's worth out of it. 
There are already better machines that'll do more for less, by the time mine ever wears out it'll be getting pretty obsolete and I'll want to upgrade to a newer one anyway.

That's what I think about running an operating system in flash,
Regards, Herman :)

---

### Post by ducksun43 on 2009-06-14
> **LoonyPhoenix said:**
> Can anyone tell me what would happen if I installed Ubuntu 9.04 on a usb stick? I mean directly, not through Unetbootin or LiveUSB creator. Is it safe for the system? Would it be a LiveUSB (i.e., would it work on other machines, not the one I installed it from)? Would it take more/less space, would it be fater/slower than traditional LiveUSB? Other advantages/disadvantages over a LiveUSB install?

Thanks in advance.

that [http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#install_debian_from_USB_stick](http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#install_debian_from_USB_stick) is isntalling Debian from USB stick but then, if you want to run your Ubuntu from the stick (i.e. not install a Desktop system with it) the process of getting the data onto the stick is the same as this link shows

---

### Post by Herman on 2009-06-14
> that [http://sunoano.name/ws/public_xhtml/...from_USB_stick]("http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#install_debian_from_USB_stick") is isntalling Debian from USB stick but then, if you want to run your Ubuntu from the stick (i.e. not install a Desktop system with it) the process of getting the data onto the stick is the same as this link showsCool! :D

Here's a little script I wrote for recording how many writes to disk I have made, I run this script just before shutting down if I remember to.
```
#!/bin/bash
# a script for recording writes to disk, (mainly useful for predicting the lifetime of flash memory)

date >> iostat.log
uptime >> iostat.log
echo " " >> iostat.log
iostat -p >> iostat.log
iostat -kdx >> iostat.log
echo "x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x=x" >> iostat.log
```I was using the data I was collecting for playing with the equation from the following link, [Accurately judging endurance for solid-state storage]("http://www.edn.com/article/CA6298274.html").

This script was inspired by a discussion with Patb in an earlier thread,                           [Installing into a SSD]("http://ubuntuforums.org/showthread.php?t=939546&highlight=iostat"), and Patb deserves most of the credit. 
I haven't been able to prove anything much yet, except that the results seem to vary dramatically according to the kind of work the user is doing.

On a slightly different aspect of the same topic, a lot of people advise the use of ext2 rather than ext3 or ext4 for flash memory, so as to avoid file system journalling. In the following linked web blog,  [Archive for the ‘SSD’]("http://thunk.org/tytso/blog/category/computers/ssd/") - Thoughts by Ted, Theodore Tso' (the head developer of the ext series of file systems),  says he thinks the benefits of file system journalling outweight the benefits of any reduction in the number of disk writes. (At least that's my interpretation of that part of his blog). 

The new ext4 file system is (as far as I know), the most advanced file system at this time for flash memory, Ext4 has support for the ATA TRIM command, which most SSD drives or memory sticks themselves don't even support yet. Look for that feature next time you're shopping for a new SSD or flash memory stick though. I'm not sure how long it'll be before it's widely implemented, but it's coming. [From ext3 to ext4: An Interview with Theodore Ts'o]("http://www.linux-mag.com/id/7272")

Regards, Herman :)

---

### Post by casperneedshelpoften on 2009-07-14
> **ducksun43 said:**
> that [http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#install_debian_from_USB_stick](http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#install_debian_from_USB_stick) is isntalling Debian from USB stick but then, if you want to run your Ubuntu from the stick (i.e. not install a Desktop system with it) the process of getting the data onto the stick is the same as this link shows

Hello Herman,
got a question almost relating to your posts here.
My laptop is:
eeepc701sd/xp 8.0 gig ssd 512 ram.
seagate 1000 gig usb 2.0 external hdd.

I am unable to write read from the ssd with any partition tools.
Windows xp installer sees the drive but unable access it.
I can run livecd usb on it when i try to install onto the ssd i get responses of unable write/read. is there a way of installing to the seagate drive? as the attempt i did gives an error on loading of:
 grub 1.5 ... loading

grub error 2

help if you can please...
thanks in advance if you can
Adam.

---

### Post by Herman on 2009-07-14
I don't know why your USB external hard drive (Seagate) would give GRUB Error 2, but certainly you should be able to easily install Ubuntu in it and use it to run your eeepc.
You should be able to install in it in the normal way, as if you were installing to an internal hard drive, but try to install GRUB to the USB drive's MBR and not to MBR in your first internal hard disk. It sounds like you've done that part okay.

I have an eeepc here too and I think it's great! It boots and runs Ubuntu in USB flash memory sticks without any problems. It's a little bit unusual in the way it decides on the drive order sometimes, but other than that no problems.

I found out mine won't boot a USB external 2 1/2" hard disk drive. However, I can use a larger USB external 3 1/2" hard disk.
I think probably it can't boot the 2 1/2" because the 2 1/2" drive relies on power from the USB port, and the eeepc doesn't have enough amps in the USB ports to power the drive. The 3 1/2 " USB enclosure has its own power lead for getting power from a power point, and a USB flash memory stick doesn't draw very much power at all.  Could a lack of power from the eeepc have anything to do with your booting problem? Is the external hard drive spinning up properly?

Are you using an older version of GRUB? The GRUB from Ubuntu Hardy and earlier have trouble booting Intrepid and later because of changes in the ext3 file system. That's the only thing I have ever heard of giving an error 2, although there may be other causes of GRUB error 2 that I don't know about yet. There's always something more to learn ...

---

### Post by Herman on 2009-07-14
Have you tried using [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli") when trying to boot your USB external hard disk after installing Ubuntu? Often you can get GRUB to boot an operating system or at least find out more information about your problem(s) by using GRUB as a mini operating system.

[Parted Magic]("http://partedmagic.com/") is the most advanced disk and partition toolbox I know of and they do make a USB version. It might be worth trying the some of the tools in that for working on your Eeepc's SSD drive with if you haven't already. I wouldn't put any faith in Windows XP's installer. You should avoid using Windows disc partitioning tools, they have a bad track record for writing garbage to partition tables, especially the Windows XP disc manager. It could be that the SSD in your eeepc only has a small partition table problem. If that's the case, it would be easy to fix with TestDisk in Parted Magic. [TestDisk Page]("http://members.iinet.net.au/%7Eherman546/p21.html").

---

### Post by casperneedshelpoften on 2009-07-15
> **Herman said:**
> Have you tried using [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli") when trying to boot your USB external hard disk after installing Ubuntu? Often you can get GRUB to boot an operating system or at least find out more information about your problem(s) by using GRUB as a mini operating system.

[Parted Magic]("http://partedmagic.com/") is the most advanced disk and partition toolbox I know of and they do make a USB version. It might be worth trying the some of the tools in that for working on your Eeepc's SSD drive with if you haven't already. I wouldn't put any faith in Windows XP's installer. You should avoid using Windows disc partitioning tools, they have a bad track record for writing garbage to partition tables, especially the Windows XP disc manager. It could be that the SSD in your eeepc only has a small partition table problem. If that's the case, it would be easy to fix with TestDisk in Parted Magic. [TestDisk Page]("http://members.iinet.net.au/%7Eherman546/p21.html").

Howdy there Herman,
My seagate drive is a/c powered it will boot on another desktop that i have no problems. but that said it still not boot eeepc... will try to re partition it into smaller partition at the beggining to see if that helps.. will let you know of results....

thanks again.... Adam.):P


edit: here
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa726e6de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496   83  Linux
/dev/sdb2          120768      121601     6699105    5  Extended
/dev/sdb3            3648        4284     5116702+  83  Linux
/dev/sdb4            4285      120767   935649697+  83  Linux
/dev/sdb5          121420      121601     1461883+  82  Linux swap / Solaris
/dev/sdb6          121094      121397     2441817   83  Linux
/dev/sdb7          121398      121419      176683+  82  Linux swap / Solaris
/dev/sdb8          120768      121071     2441817   83  Linux
/dev/sdb9          121072      121093      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         244     1956832+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(242, 254, 63) logical=(243, 157, 42)

Disk /dev/sdd: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x414f414e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         244     1956832+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(242, 254, 63) logical=(243, 157, 42)

hope that helps..

---

### Post by casperneedshelpoften on 2009-07-17
Quote:
                                                                      Originally Posted by **Herman**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7615825#post7615825")                 
                 Have you tried using [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli") when trying to boot your USB external hard disk after installing Ubuntu? Often you can get GRUB to boot an operating system or at least find out more information about your problem(s) by using GRUB as a mini operating system.
tried this but grub just hangs:
Grub..


and then nothing. I have reformatted the drive re-installed jaunty 9.04 and it boots the desktop no worries.... but eeepc still only gets grub error 2......  more suggestions please

---

