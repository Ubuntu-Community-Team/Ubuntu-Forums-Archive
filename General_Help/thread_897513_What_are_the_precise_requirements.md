---
title: "What are the precise requirements?"
date: 2008-08-22
forum: General Help
---

### Post by rogare on 2008-08-22
I am thinking about adding Ubuntu to my computer (currently I use Windows XP) and I wanted to know what are the full requirements for installing Ubuntu. The most important requirement for me is the hard drive space needed, because I need to know if I have to buy a new one.

---

### Post by WRDN on 2008-08-22
The minimum amount of HDD space required is 4Gb.

> **_Bare Minimum requirements_**

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

**_Recommended minimum requirements_**

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection 

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 

[Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by coffeecat on 2008-08-22
Why not post some details of your present hardware, and then people can comment? Apart from minimum system resources, it's also worth considering specific aspects of the hardware. Although hardware support in Ubuntu is excellent, there are some chipsets for which no or inadequate drivers are available. Things to avoid are SiS motherboard chipsets, some (but not all) ATI graphics cards and some wireless chipsets. Again, post details of your hardware and we can see if anything is likely to be a problem.

Another thing to do is to download the live CD iso (if you have not already done so), burn this to disc and try booting up with it. You have nothing to lose except for about 650Mb bandwidth and the disc and you will be able see whether Ubuntu will run on your present hardware. The live CD won't change anything on your hard drive, or affect Windows, unless you want it to, so it's quite safe to run as a try out. Just bear in mind that running from the CD is very slow - it does not do justice to how it will run from a HD installation.

---

### Post by rogare on 2008-08-22
First of all, I don't know all information about the hard drive, but it is a regular one so I don't worry. Another question - can I install it on another hard drive and not C? Like E, or F?

---

### Post by WRDN on 2008-08-22
> **rogare said:**
> First of all, I don't know all information about the hard drive, but it is a regular one so I don't worry. Another question - can I install it on another hard drive and not C? Like E, or F?

You can install Ubuntu on any HDD, providing there is sufficient space. Also, the use of single letters (drive C, E, and F etc) is a Windows convention. In Ubuntu, you will see "/dev/sdaN" or "/dev/hdaN" instead (where N represents a number).

---

### Post by rogare on 2008-08-23
I got another question (sorry if I am annoying). Let's say I install Ubuntu on E: ("/dev/hda2" for example), will it interrupt the normal use of E: ? I will still be able to use it, or it will be locked for Ubuntu or something?

---

### Post by meindian523 on 2008-08-23
Installing Ubuntu on E partition(not Hard drive) will remove all data on E partition because Ubuntu's system files will reside there.

---

### Post by rogare on 2008-08-23
Well, what **are** partitions? Can I add partitions in my E hard drive, so I will have data and Ubuntu on the same hard drive?

---

### Post by meindian523 on 2008-08-23
[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

What you call E hard drive is actually E partition on your hard drive.

---

### Post by mb_webguy on 2008-08-23
Well, a drive letter is just a mount point, so C: and E: could be either separate drives or separate partitions on the same drive.

One thing that will help us answer your questions and give you the best advice on how to install Ubuntu on your system with the least trouble possible is to go to Disk Management and tell us what you see there, as far as number and size of disks, and number and size of partitions (divisions) of the disks.

---

### Post by rogare on 2008-08-23
I don't have any Disk Management (from a short research I found out it is a program added to Windows only in the Vista version (here: [http://en.wikipedia.org/wiki/Partition_(computing)#DOS.2C_OS.2F2.2C_and_Windows]("http://en.wikipedia.org/wiki/Partition_(computing)#DOS.2C_OS.2F2.2C_and_Windows")). How do I check if my E: and F: are real disks or partitions?

---

### Post by Gondee on 2008-08-23
Just burn the live CD and boot from it. There is a graphical interface that will start and and icon on the desktop that says install. double click it.
Those are you options. Rember that if you install it, even on another drive, to be carful where the grub is installed. You dont want to mess with your other drive



Heres another option. [http://wubi-installer.org/](http://wubi-installer.org/) This will allow you to install it on your hard drive without going through any partion screens or messing with anything. When you done with Ubuntu you can simply uninstall it in windows as you would a normal program.

But if you do insist on installing ubuntu through the live CD. Then For the safty of your windows hard drive, remove it from your computer physicaly. This way nothing will happen accdently.

---

### Post by rogare on 2008-08-23
Anyway, I read around some guides in the documentaion and got some advices from people that know a bit about computers, and I have this question: If I use the partition option in the Ubuntu install like in [this guide]("https://help.ubuntu.com/community/forum/installation/Partitioning"), is there any danger to my current disks?

P.S.: I am also considering now using [LiveCD persistantly]("https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence") or Wubi, but if I do can I install programs like PHP and MySQL on Ubuntu in those modes?

---

### Post by rogare on 2008-08-24
Anyone knows?

---

### Post by ad_267 on 2008-08-24
I think you should be able to use MySQL and PHP with Wubi but I'm not sure. Don't know about liveCD persistance. I say set up a dual boot by making some room for Ubuntu on a drive or partition somewhere.

The only real danger is if you accidentally do the wrong thing, which isn't very likely. As long as you make sure that you are only resizing the partitions you want you should be ok. Gparted never does anything without listing everything it is going to do and getting your OK.

---

### Post by rogare on 2008-08-24
Let's say I'll use the Partitioner in the Ubuntu installer and choose the option "Resize and use freed space", and then I try to make the Windows part smaller than what it currently use (For example now I have 130GB used, out of 233GB) and I leave the Windows with 120GB - what will happen? I won't be able to scroll beyond 130GB, or I'll get an error or it'll delete files?

---

### Post by ad_267 on 2008-08-24
> **rogare said:**
> Let's say I'll use the Partitioner in the Ubuntu installer and choose the option "Resize and use freed space", and then I try to make the Windows part smaller than what it currently use (For example now I have 130GB used, out of 233GB) and I leave the Windows with 120GB - what will happen? I won't be able to scroll beyond 130GB, or I'll get an error or it'll delete files?

I think the installer won't let you. It's pretty smart.

Also it's a good idea to defragment the drive from in Windows first.

---

### Post by rogare on 2008-08-24
So by what you say using the partitioner is very safe? (Of course I'll back up my files, but anyway...)

---

### Post by meindian523 on 2008-08-24
> **rogare said:**
> I don't have any Disk Management (from a short research I found out it is a program added to Windows only in the Vista version (here: [http://en.wikipedia.org/wiki/Partition_(computing)#DOS.2C_OS.2F2.2C_and_Windows]("http://en.wikipedia.org/wiki/Partition_(computing)#DOS.2C_OS.2F2.2C_and_Windows")). How do I check if my E: and F: are real disks or partitions?
Nopes,in XP,you can access Disk Management by right clicking My Computer and clicking Manage.

---

### Post by ad_267 on 2008-08-24
Well yes but I would recommend to use the manual option and first set up the partitions with gparted on the liveCD as then you have a lot more control over where everything goes.

There's a good guide here for installing Ubuntu: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by rogare on 2008-08-24
Yes, I found this - but from what I understand the Partitioner in the installer is safer (also from some guides I found in the documentation). I just want to know how safe it is.

---

### Post by ad_267 on 2008-08-24
> **rogare said:**
> Yes, I found this - but from what I understand the Partitioner in the installer is safer (also from some guides I found in the documentation). I just want to know how safe it is.

It is safe but with partitioning there's always a small possibility that something will go wrong so it's always advised to back up any important data.
I think some of the problems people have with the partitioner are due to not understanding the layout of their hard drives and partitions and what they actually need to do so if you understand what partitions you need then you will be fine.

---

### Post by rogare on 2008-08-24
Last question (I realy hope... I want to install Ubuntu :) ) - If I use the partitioner to cut some of my hard drive for Ubuntu, this partition will be only system files of Ubuntu (if I understood right), so where I can put **my** files?

---

### Post by ad_267 on 2008-08-24
It will create a /home directory (where you put your documents) automatically. Many people create a separate partition for the home directory but this isn't required. You also need to have a swap partition. This will be taken care of if you use the installer. If you use manual partitioning you just need to make a swap partition about twice the size of your ram.

You will be able to access your windows drive too so if you want you can keep most of your documents on the windows drive and create links to there from your home directory.

---

### Post by rogare on 2008-08-24
My last post (I realy hope now :) ) - So if I give Ubuntu 60GB, he'll make a swap partition of 2GB (left with 58GB) put his system files which are lets say 4GB (left with 54GB) and will give me 54GB of free space to use?

---

### Post by ad_267 on 2008-08-24
> **rogare said:**
> My last post (I realy hope now :) ) - So if I give Ubuntu 60GB, he'll make a swap partition of 2GB (left with 58GB) put his system files which are lets say 4GB (left with 54GB) and will give me 54GB of free space to use?

Yup that's what I understand. I've only used the manual partitioning option though so I don't know if it gives you a choice about the size of your swap or not.

Also don't worry about posting if you need more help :)

---

### Post by rogare on 2008-08-24
Could you explain how the manual partitioning works (or looks)? I didn't find any images of this.

---

### Post by ad_267 on 2008-08-24
I remember I found a good guide that explained it when I first installed Ubuntu but I can't find it now.

Theres this here that explains partitioning schemes:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

And here's the guide for using gparted:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

You go to system - administration - partition editor in the live cd to open it up and then you want to create an ext3 partition for Ubuntu and a swap partition. I've attached screenshots of my partition scheme so you get an idea of what it should look like. I have a separate hard drive for my /home partition but like I said before you don't need this and Ubuntu will automatically make a home directory for you.

Don't worry about playing around with gparted and resizing because nothing is actually applied until you click on the apply button and confirm the operations.

---

### Post by rogare on 2008-08-24
If I want safe and simple installation - what do you reccomend? Partitioning myself, or letting Ubuntu do this?

---

### Post by ad_267 on 2008-08-24
If it was me I would recommend partitioning yourself because you know exactly what the partitioner will do. I've heard of some problems where  the automatic installer was doing things differently to what people thought.

I just found this thread here that looks like it could be helpful: [http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

He recommends making space in Windows and then using the manual install option and setting up the partitions in the installer.

I'm not sure what the advantage of the gag boot loader is though, you don't need that.

---

### Post by rogare on 2008-08-24
I think I'll trust Ubuntu (after backing up my data) and use its partitioner. Now I add an after-install question - how will I choose whether I want Windows or Linux every time? I guess it isn't a simple option like "Switch user" in Windows :)

---

### Post by ad_267 on 2008-08-24
Yup both options are just as safe, I'm pretty sure they use the same partitioning software so there isn't really that much difference. There's just more options and control with the manual method which does make it a bit more difficult.

You can select whether to boot Ubuntu or Windows when you turn on your computer. You will get a menu that looks something like [http://en.wikipedia.org/wiki/Image:GRUB_screenshot.png](http://en.wikipedia.org/wiki/Image:GRUB_screenshot.png) except there will be an option to select Windows.

So if you want to switch from Windows to Ubuntu you have to restart your computer. Ubuntu will be set as the default operating system but you can change the default operating system that is loaded by editing the /boot/grub/menu.lst file in Ubuntu by pressing Alt+F2 and running "gksu gedit /boot/grub/menu.lst" and setting the "default 0" line to "default saved". You have to do it that way to run the text editor as the root user otherwise you wouldn't be allowed to edit the file.

---

### Post by rogare on 2008-08-24
Well, I guess all I have to do now is back up, clean some junk and install? :)

---

### Post by ad_267 on 2008-08-24
> **rogare said:**
> Well, I guess all I have to do now is back up, clean some junk and install? :)

Yup and don't forget to defragment the drive you want to resize.

It is kind of scary at first changing partitions around if you haven't done it before but hopefully pretty soon you'll be booting up Ubuntu and exploring!

I recommend the first thing you do once your up and running is read about installing software in ubuntu because it is a bit different to Windows. There's a great site at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but it seems to be down at the moment. You can do a google search for "monkeyblog how to install anything in ubuntu" and view google's cached version of the page though.

---

### Post by rogare on 2008-08-24
About the defragment, I have one physical disk which in Windows is shown as 3 different disks - C, E and F. What should I defragment?

Edit: Also, after I do the resize and install, I will be able to use files in what now called disks E and F, or I'll have to move them somehow else?

---

### Post by rogare on 2008-08-24
Anyone?

---

### Post by rogare on 2008-08-24
Bump.

---

### Post by meindian523 on 2008-08-24
Please be patient and bump only if you don't get replies until after 24 hours from your last post.
About your question:
Defrag C: and move your data on E: and F: someplace safe before you install.Same goes for data on C: too,in case you make a mistake while installing.

---

### Post by rogare on 2008-08-24
Thanks you. Sorry for the double-bump, I didn't know the rules.
Still I ask, if I install Ubuntu, will I be able to read files that now are in my "Windows" drives (C, E and F).

---

### Post by jakupl on 2008-08-24
> **rogare said:**
> Thanks you. Sorry for the double-bump, I didn't know the rules.
Still I ask, if I install Ubuntu, will I be able to read files that now are in my "Windows" drives (C, E and F).

Yes you will, but windows will not be able to read the ubuntu partition.

---

### Post by meindian523 on 2008-08-24
Yes,provided you don't select any of the partitions C:,D: or E: for installation.If you do,your files will be overwritten and lost forever.

---

