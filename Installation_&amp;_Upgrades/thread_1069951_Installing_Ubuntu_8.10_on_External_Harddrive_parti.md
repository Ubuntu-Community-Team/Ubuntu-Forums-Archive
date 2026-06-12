---
title: "Installing Ubuntu 8.10 on External Harddrive partition"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Jarige on 2009-02-14
I'm trying to install Ubuntu 8.10 using a LiveCD (which I'm currently booted on) on my external harddrive. I already made a partition (50MB out of 300MB total) on my external hdd using Windows (NTFS).

I've followed instructions of this site [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)
But it didn't work. In the menu 'Make USB Startup Disk' my partition(s) doesn't show up.

I hope you guys can help me. Today is my first time I booted Xubuntu and Ubuntu, and I can't wait to use them:)
Vista sucks:)

Appreciated:)

Jarige

---

### Post by Jarige on 2009-02-14
BUMP
One guy got 17 replies in the first minute he posted his message, and I waited 15 minutes already, no reply at all... This doesn't seem like a hard question to me?

---

### Post by ajgreeny on 2009-02-14
>  I already made a partition (50MB out of 300MB total) on my hdd using Windows.Did you really mean this;only 50 megabytes (or MB as you wrote)?  Perhaps you meant 50GB, but if not the problem is simply that ypu do not have enough space to install ubuntu.  A basic install without any of your own docs or photos etc etc, will take about 2.6GB as far as I can remember.  50MB will not even hold the kernel, never mind all the desktop extra stuff that ubuntu and any other distro needs.

---

### Post by ve4cib on 2009-02-14
50MB isn't even enough for a command-line installation; the smallest those go is about 700MB with Ubuntu.

Assuming you meant "GB" why are you making a Live installation on your external HD?  Wouldn't it be easier to do a proper install to the HD?  It would certainly boot more quickly.

---

### Post by Jarige on 2009-02-15
Oh ****, I meant 50GB out of 300GB of course, sorry :P
Dude that was stupid, really.
I know that installing on my harddrive might be smarter, but when someones computer crashes or something, I can help him with recovering data and stuff if its on my external hard drive. (So I won't need the cd, which can be broken or something)

And I like it being on my exhdd :P
It just seems more safe to me, and I don't really know, but I want it on it :P
I don't really care about boot time, cause I know it will be faster then Vista. And btw, my external harddrive is nearly as fast as my normal harddrive(s). So it shouldn't matter that much.

But no help so far, anyone has the same problems or has solved them?

---

### Post by Jarige on 2009-02-15
Bump

---

### Post by cosine352 on 2009-02-15
did you check with the partition editor? 
System ---> administration --> Partition Editor

or 

sudo fdisk -l

---

### Post by beatgr on 2009-02-15
Jarige -

I could not figure out what you were trying to do.
After some additional posts and details, I THINK you desire to have a USB "bootable" Flash drive or external hard drive.

1. This works with computers with BIOS (and Setup menus) that support bootable USB devices.  For those computers without this BIOS option, you have to create a specific CD to permit this functionality.  I would perform this step and enclose as part of your restoration "kit":
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

2. When you partitioned and formatted this external hard drive under Windows, I assume the NTFS file system was selected (not FAT/FAT32).

3. When you used the Ubuntu v 8.10 LiveCD, did you have the external USB drive plugged in and powered up?

4. These are the steps for a USB flash drive
[http://www.pendrivelinux.com/usb-ubuntu-810-install-from-windows-non-persistent/](http://www.pendrivelinux.com/usb-ubuntu-810-install-from-windows-non-persistent/)

SUGGESTION.
Are you aware of this tool?: UNetbootin
This tool works under Ubuntu and MS Windows
Permits usage of many distros to create USB/exteranl hard drive versions.
UNetbootin (Universal Netboot Installer) is a cross-platform utility that can create Live USB systems and can load a variety of system utilities or install various Linux distributions and other operating systems without a CD.
*This might be the ideal tool (Swiss Army knife) you are seeking*
[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

Here is their web site:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

good luck with it!

g. beat

---

### Post by Jarige on 2009-02-15
Thanks for your replies.

1. I probably have the option to boot from USB, cause my laptop just nearly one year old. I didn't check that though.
2. Yes, it was NTFS.
3. It was plugged in, and powered up, and I could see its contents on both of the partitions (one was empty of course) but I just couldn't select it from the list in the menu 'Make USB Startup Disk' (like I said)
4. Thanks for the link, but I want it to be persistent. I want it to safe data and options.

I don't think UNetbootin is a good tool for me, I don't want some Live USB which can install a lot of Linux distro's, I just want to boot Ubuntu on my external hard drive, which safes data and options. My friend has done it, but he's on a holiday now, so I can't ask him:(...

cosine352, I don't really know the purpose of opening partition editor for my problem. And I tried 'sudo fdisk -l' but how should that help me?

Well I hope I can get more reactions :) Thanks for the reply guys.

---

### Post by redroad55 on 2009-02-15
by opening partition edittor like stated above it will show all drives and how they are partitioned so you can see how yow and where you want to place the Ubuntu OS .. On live cd > applications > system > admin. > Partition editor .. Post back what you find and it will be easier for others to help..

---

### Post by Jarige on 2009-02-15
I'll boot the LiveCD right away.
I'll post results in a few minutes.
Thank you...

---

### Post by Jarige on 2009-02-15
Well I opened GParted, and it shows my 3 drives and their partitions, but its a little hard to copy and paste their contents, so I did sudo fdisk -l and it shows this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bda47a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18356   147444538+   7  HPFS/NTFS
/dev/sda2   *noboot*        18357       19457     8843782+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0adc4429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1 *noboot*              1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3414533

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1 *noboot*              1       32386   260139840    7  HPFS/NTFS
/dev/sdc2   *       32386       38914    52428800    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

So this is my current set up, and just in case these are the labels:

/dev/sda1    OS
/dev/sda2    HP_RECOVERY

/dev/sdb1    DATA

/dev/sdc1    FREECOM HDD
/dev/sdc2    Ubuntu

Ubuntu is (obviously) the partition where I want Ubuntu to be installed to. sdc is my external hard drive, but you might have figured that out on yourself:P.

Much appreciated.
Note: I'm a noob at Ubuntu, so plz don't make it too complex :)

Thanks.

edit: I added *noboot* on the places that where empty indicating that it wasn't boot. Hopefully it will make it a bit better.

---

### Post by redroad55 on 2009-02-15
one other question on hardware .. So your hard drive with the windows OS is master or is a sata drive correct ?..The external drive is in a external drive box connected via usb correct? Is the external drive a sata drive?

---

### Post by Jarige on 2009-02-15
I've got a laptop, never opened it up, and I'm no expert with hardware. My OS harddrive is probably SATA, I dunno. External HDD is a USB drive, no SATA, it just has a cable which you plug in to a USB port. Actually this is a link to the hard drive I own: [http://www.freecom.com/ecproduct_detail.asp?ID=3887&CatID=8020&sCatID=1146187&ssCatID=1148416](http://www.freecom.com/ecproduct_detail.asp?ID=3887&CatID=8020&sCatID=1146187&ssCatID=1148416)

But what has that got to do with installing Ubuntu on it?

---

### Post by Jarige on 2009-02-15
BUMP (before I go to bed, I'll check again tomorow, thanks for the help so far. I really learned a lot already, and thats exactly why I wanted to try this:))

---

### Post by redroad55 on 2009-02-15
prior to sata, hard drives had to be designated master or slave .. just eliminating possible conflicts that can be ruled out with a few questions ..  The confusion arises here in whether the bootloader for linux will allow you to dual boot from a external usb connected hard drive .. I don't know the answer to that question .. the link you provide at the begining post is for a thumb drive so I am a little confused about how you got to where you are but no worries .. so other than the 50 gb that you partitioned already on the external how is the remaining space on the external drive used or better yet how do you want it used?

---

### Post by Jarige on 2009-02-16
The remaining space is currently in use by programs, a lot of games and a lot of stuff I really don't want to lose if I've got the choice. There's no data which is needed for school or something, so its not THAT precious. I just don't want to lose it, and I lack the space to store it anywhere else. (I might ask my brother for the storage in his laptop though, but I don't want to do that unless it must be done)

FREECOM HDD: Total 248.1GB     Used: 187.8GB   free: 60.2GB

(I splitted the Total freespace (the 2 partitions together) which was about 110GB, and I decided that about half should be for Ubuntu (50*1024MB exactly))

Hope this helps make it clearer, if I didn't really answered your question, ask more specific. 

Thank you

---

### Post by Jarige on 2009-02-16
I really didn't go far with the tutorial in the first post. I just created partitions, and I booted Ubuntu from the LiveCD, thats all I got right now. But I think that tutorial shows how to make a LiveUSB, which is NOT what I want.

---

### Post by redroad55 on 2009-02-16
Hi , We must be on different time zones ... First we make sure you are certain of the partition designation for the partition you created .. I believe it is /dev/sdc2 from your previous post .. Now being certain of that we can begin .. Insert the OS live CD > click on install > the install will ask you a series of questions which you answer and then you will come to the part of partitioning , there you will choose manual > Now you will see the partition layout of your system .. Identify /dev/sdc2 > click on /dev/sdc2 and choose delete , this will then show up as free space > now click on free space > then click on new partition > designate it as primary ...then size it to 8000 (8.0 gb) and make the mount point " / "  > after this partition is created you will see the remaining free space .. we are going to make another partition for the swap area .. click on free space > click on new partition > designate it primary ..size it to 2000 ( 2.0 gb) and now choose " swap area " for its designation > after this partition is created we go to make our final partition by going to remaining free space as before.. Click on free space > click on new partition > designate this time as logical ( So if you want to expand with another drive in the future ) .. The number for size will be exactly what shows,so no change on that number ... this will be designated as " /home " for mounting point ... Now you are done with the hard stuff just let the normal install procedure continue ...Post back If you have any results and or questions .. Best to you

---

### Post by kkilps on 2009-02-16
unmount the external harddrive, then click install and make sure you use the external to install. Unmounting it allowed me to use it.

---

### Post by linuxisevolution on 2009-02-16
Just unplug your internal hard drive and run the livecd. Then do the install like you normally would, but select your external drive. I did the same thing with a USB flash disk when installing debian. :)

---

### Post by redroad55 on 2009-02-16
Why have a /home partition ? Lets say 2 years from now you want to install a newer kernel because it supports some features that are not supported on your present kernel ... You can't do it very easily with out loosing your files  unless you have a pre designated /home partition..Just a thought to consider because you only get one shot at this ..

---

### Post by trepid666 on 2009-02-16
Hi, I just finished installing Ubuntu on my external HD and its great!

So what I did, is went into BIOS and set it to boot from:

1)CDrom
2)USB device
3)Removable Media
4)Main Hard Drive
5)Boot to LAN

After that, still in BIOS, enable Legacy USB, i don't know if its neccessary but i selected OS other instead of OS msdos

I removed my internal HD and popped in the LiveCD, reboot and voila.

I selected manual partitioning and on the last step before installing, click advanced and saved the bootloader on a seperate partition. Only has to be like 200MB.

Good Luck, let us know how it goes.

---

### Post by Jarige on 2009-02-17
Thanks redroad55, your post looks very promising. I hope that will work. Unfortunatly, I just had a LAN party during night, so I'm pretty tired now. GTG home first, then sleep. Maybe in about 6 hours I'll try your post. I hope its clear enough for me, I'm really a beginner.

Thank you very much, I'll keep you updated.

---

### Post by Jarige on 2009-02-17
Thanks trepid666, but what you did was after the install, while my post is about the install. Thanks anyway.

---

### Post by Jarige on 2009-02-17
Currently installing :D. Did exactly what redroad55 told me to do. Including the /home.
But what exactly is going to happen to /home? Are my documents going to be stored there? Cause my documents are currently in 'FREECOM HDD'  (sdc1) and I don't need them to be on the /home, and 40GB is a bit too much for just documents :P. Or is /home for applications just like wine (I really want that) and stuff?

I can always make /home smaller can't I? And designate the free space to 'Freecom HDD'?

Ah well, I hope to inform you about my first Ubuntu boot from my external harddrive in a few minutes! :D

Thank you so far, for the help. Especialy you redroad55 ;)

---

### Post by Jarige on 2009-02-17
Hmm, now I think of it, you might as well explain why the 'type'  is ex3 or something like that, and what the '/'  and swap file are for.
I guess the / is where Ubuntu is installed, but what is swap file? Is that something like the hibernate file in Vista? Cause I'll probably need 3GB then. But if its like virtual RAM then this should be fine I guess...

---

### Post by redroad55 on 2009-02-17
/home is where all files and settings that are user specific are stored they will be of course Ubuntu generated .. virtual ram would be accurate description.. "/" is the root , kernel

---

### Post by Jarige on 2009-02-17
Ok, install went fine, no errors. But when I rebooted the system, it gave errors; it said:
Grub Loading, please wait...
Error 22

So I rebooted
Then it said:

Grub Loading, Please wait...
Error 21

Reboot; error 22
Reboot; error 21

Weird?

So, I rebooted again, and pressed F9 to change boot order, and put USB harddrive above my 'netbook harddrive'. Then rebooted, and I found this error:
Operating System not found

I got a little scared seeing that actually. So, I tried to open 'OS' and he gave me this message:
[ [img]http://willhostforfood.com/users/J/Jarige/Cannot mount volume.png[/img]](http://willhostforfood.com/access.php?fileid=55208)

Then I suddenly got another message:
[ [img]http://willhostforfood.com/users/J/Jarige/Unable to mount OSpng.png[/img]](http://willhostforfood.com/access.php?fileid=55209)

What to do? I can't boot Vista nor Ubuntu, I can just use the LiveCD again, to go to this forum.
This is the output of sudo fdisk -l:
```

ubuntu@ubuntu:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bda47a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18356   147444538+   7  HPFS/NTFS
/dev/sda2           18357       19457     8843782+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0adc4429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3414533

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32386   260139840    7  HPFS/NTFS
/dev/sdc2           32387       33382     8000370   83  Linux
/dev/sdc3           33383       33631     2000092+  82  Linux swap / Solaris
/dev/sdc4           33632       38913    42427665    5  Extended
/dev/sdc5           33632       38913    42427633+  83  Linux
```

Now I really hope someone can help me. I think I saw some other threads with error 21 or 22, but I don't remember it that well. I'll search them, and hope to find the answer elsewhere, if I don't, I guess I'll have to wait for another respond and get bored cause I can't play games:(
Other things that are a bit strange, is that I can't mount FREECOM HDD either, while I can mount the other partitions. I can mount DATA, and I can acces my documents there (phew) and I immediately backed them up on an USB stick, so those are safe.
I will no try to reboot the LiveCD to see if I can mount the FREECOM HDD then. (I want to see a video on it)

Thanks for your help so far.:)
Stay optimistic :)

---

### Post by Jarige on 2009-02-17
Bump

---

### Post by Jarige on 2009-02-17
I wanted to make it a little more clear:

When I boot, and the CD is in; boots LiveCD correctly
When I boot, and my USB Harddrive is in; Throws 'Operating System not found' error
When I boot, whithout CD and USB (from local HDD) Grub gives either error 22 or 21 (alternating, not both at the same time)

Thanks :)

PS I don't know how to change the title of the thread, but I would like to change it to 'Grub error 22 or 21' or something like that. Anyone knows how:p

---

### Post by Jarige on 2009-02-18
BUMP. Damn, I thought there would be a reaction after I went to bed.
Well, its almost 11 o'clock in the morning now, I think I got to wait now...
Or I'll go try and make World of Warcraft work with Wine :) I'll do that, in the meanwhile, I'll check this Thread regulary.

---

### Post by Jarige on 2009-02-18
BUMP again

---

### Post by Jarige on 2009-02-18
Since the install went correctly, I guess this thread is solved, there's still an error so I created a new thread. Hopefully the new title will pull more people there, nobody seems to help me here.
This is the new thread: [http://ubuntuforums.org/showthread.php?p=6754885#post6754885](http://ubuntuforums.org/showthread.php?p=6754885#post6754885)

Thank you.

---

### Post by Jarige on 2009-02-18
*solved* YEY!

Thanks for your help guys. You are great :D

---

