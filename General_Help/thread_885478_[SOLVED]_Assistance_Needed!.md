---
title: "[SOLVED] Assistance Needed!"
date: 2008-08-10
forum: General Help
---

### Post by Yezinki on 2008-08-10
Hi there,

You must have read a few of my posts...am totally new to Ubuntu & Linux versions....Have installed Ubuntu hardy on my Sony Vaio....btw dont have a clue how it got installed.....have lots of queries......at the moment trying to familarize myself with Ubuntu but would like to ultimately Dual boot Vista/XP & Ubuntu.

My email is [email]nabid65@hotmail.com[/email]

Regards,

Yezinki.

---

### Post by dexter.deepak on 2008-08-10
you should rather try to be more specific regarding your problems.
you cant learn evrything in a single day..so you should be looking to learn one thing at a time.
just jot down your current problems, and ask them one by one over here, only then you can expect to get some fruitful replies....not a lame one like this :lolflag:

---

### Post by Yezinki on 2008-08-10
Thanks deepak I appreciate your advice.

Kindly give your expert opinion regarding a few queries I have posted.....like Drive, Pidgin Cheese etc.

Regards!

Yezinki.

---

### Post by Yezinki on 2008-08-10
Partition making, Swap file, TV Tuner device, Firmware erroe on start up...

---

### Post by bigbrovar on 2008-08-10
cool i have some experiences with Sony Vaio .. and i would be more than glad to offer my help ... i used the sony vaio fz21e adn so far i got it to rock well on ubuntu .. what is the name of your Vaio ? .. well one thing u should bare in mind is that sony notebooks are very Linux Unfriendly .. but it some tweaks u would get it to work .. one area u might have problems is ur webcam if u have one .. but that also can be sorted out .. u can check this site [http://www.palmix.org/vaio-en.html](http://www.palmix.org/vaio-en.html) it really helped me ..some of the guide might be hard for u but dont worry if u have nay problem just post it here ..

---

### Post by lisati on 2008-08-10
Where would you like to start? Which area would you like help with first?

---

### Post by Yezinki on 2008-08-10
Thanks.

1. Sony Vaio VGC-LS1

2. Post Drive......Firstly!

Regards!

---

### Post by dexter.deepak on 2008-08-10
this is a good place for knowing partitioning basics :
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

swap is a bigger issue, and i dont think you really need to know it much, but if you want to know more, then you can PM me any time.

---

### Post by Yezinki on 2008-08-10
Thanks Deepak I really do appreciate it & your allowing to PM.

Regards!

---

### Post by bigbrovar on 2008-08-10
here is where to start .. i use this guide when i wanted to start linux a year ago .. its very easy to follow and comes with screenhots .. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by vjkeito on 2008-08-10
hi,

you are going in at the deep end first without taking the time to learn from the ground up.

I would suggest learning the information out yourself when you require the need for it, and also going through some guides that cover such details.

One such place is [***Ubuntu-Unleashed***]("http://www.ubuntu-unleashed.com/"), another is [***Ubuntu-Guide***]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

Then also specific problems that you can't find out easily using google I'd ask on here or the offical Ubuntu IRC channel

hope that helps somewhat

---

### Post by Yezinki on 2008-08-10
Thanks a lot bigbrovar.

---

### Post by Yezinki on 2008-08-10
Thanks vjkeito........

---

### Post by vjkeito on 2008-08-10
Another great site (that does explain about Swap) is this one [http://www.funnestra.org/ubuntu/hardy/]("http://www.funnestra.org/ubuntu/hardy/")

if you use Firefox, just hit ctrl+F then type swap into the search box

---

### Post by Yezinki on 2008-08-10
Thanks vjkeito again.

---

### Post by vjkeito on 2008-08-10
you can thank all those that have helped you, officially using this button on the forum 
[[IMG]http://img227.imageshack.us/img227/9620/screenshot1cg4.png[/IMG]](http://imageshack.us)

---

### Post by vjkeito on 2008-08-10
> **Yezinki said:**
> Thanks vjkeito again.

not a problem ;0)

anytime.

you'll find Ubuntu is *all about community*.  we look after our own!

---

### Post by Yezinki on 2008-08-10
Hi there,

I am getting stuck at Stage 4.

Prepare disk space.

I have C primary active , size 70GB, with 23 GB of Vista etc , rest is free.

Logical is D space 25 GB.

Now here what option should I choose....Guided, Guided Entire Disk, Guided use largest free space or Manual.

Regards!

---

### Post by Yezinki on 2008-08-10
Using Manual it shows:

/dev/sda

/dev/sda1 ntfs 4000007 MB
Free space 320000 MB

/dev/sda5 ntfs.........260000 MB

Which should I high lite & use options of New partition/table, Edit partition, Delete Partition?

Regards!!

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> Hi there,

I am getting stuck at Stage 4.

Prepare disk space.

I have C primary active , size 70GB, with 23 GB of Vista etc , rest is free.

Logical is D space 25 GB.

Now here what option should I choose....Guided, Guided Entire Disk, Guided use largest free space or Manual.

Regards!

Whatever you do, do **NOT(!!!)** select to use the Entire Disk, as this will format it, and you will loose your Windows installation.
For an automated installation, use "Guided- use largest free space", although I would recommend to select Manual instead. You should create the partitions you need in GParted (System > Administration > GParted on LiveCD). You should delete the partition that you do not use and wanted to install ubuntu on (make sure you don't delete the XP partition, and if you have any questions, ask first). Then, from the free space, create a "New", "Extended" partition. From this, create 3 logical partitions inside the extended partition. You need a swap partition (2 x RAM recommended), and then create 2 ext3 partitions. The first will be used to install the OS on, and the second will be a /home partition (this is very useful if you ever need to reinstall Ubuntu). Then, during the installer, select Manual partitioning.
In the next page, you can then select the swap partition, and others. Select the partition you wish to install Ubuntu on, and then click "Edit Partition". Now, give it the mount point "/" (type this in the text box). Now, select the other ext3 partition you created, and give it the mount point "/home", using the same method as used for the partition for the system installation.

If you need to know the partition names (/dev/[name]), then open the Terminal, and type "fdisk -l".

If you have any queries, please ask before applying any partition changes, and I would recommend you backup any important data before continuing.

---

### Post by Yezinki on 2008-08-10
In Maual after deleting un required partition when I reach to creation it only gives the option of Primary & Logical........NOT extended??

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> In Maual after deleting un required partition when I reach to creation it only gives the option of Primary & Logical........NOT extended??

Use GParted rather than the partition editor in the Installer.

---

### Post by Yezinki on 2008-08-10
Created 1 Extended & in it 3 Logical.........using GParte....but installer says no Root file system defined??

Sorry to be a pain......lol

---

### Post by vjkeito on 2008-08-10
what you should do if your vista install takes up the whole disk is....

use gparted to resize the partition that vista is on, then you'll have vista on a smaller patition and you'll be left with some unpartitioned space to install ubuntu on.

once this is done then you can commence installing ubuntu.  choose "largest continuous free space" and this will then use up that unpartitioned space you've freed up before.

be very careful when doing this and take care to backup all your important data before resizing any disks!!!!

once you've installed ubuntu the next time you start Vista it may see some errors - LET IT FIX THESE ERRORS to the filesystem (that is imperative)

good luck ;0)
hope that helps!

---

### Post by vjkeito on 2008-08-10
when using manual disk setup you need to follow [these instructions]("http://www.funnestra.org/ubuntu/hardy/#install")....

I would choose guided if you don't know what you're doing and let it install to largest continuous free space as I suggested before

---

### Post by Jdm111 on 2008-08-10
> **Yezinki said:**
> Partition making, Swap file, TV Tuner device, Firmware erroe on start up...

Dont bother with the tv tuner just use Zattoo.

---

### Post by Yezinki on 2008-08-10
Whats Zattoo??

---

### Post by vjkeito on 2008-08-10
> **Yezinki said:**
> Whats Zattoo??

if you want to become a master of all that is linux you need to be prepared to go out there and do some research.

typing "Zattoo" into google brought it up straight away ;0)~
[URL="http://zattoo.com/"][B][I][COLOR="Red"]
Zattoo[/COLOR][/I][/B][/URL]

It's TV streamed to your PC, legally, without the need for a tuner card.

---

### Post by Yezinki on 2008-08-10
Thanks to WRRDN.........I installed it on my lap top with Vista.

But the system has slowed alot despite 4 GB memory with the dual boot.......both Vista & Ubuntu.

How do I find the hard drive divisions in Ubuntu........like Comp mangment in Vista........may be partioning isnt proper for you experts to view & comment.

Vista didnt give any errors but at times displayed a msg low in resources??

---

### Post by Yezinki on 2008-08-10
Even the dsl is damn slow........plus Nvidia card drivers issue

---

### Post by Sycron on 2008-08-10
For nVidia you may use the restricted drivers. How much RAM do you have, what is your CPU freq and what nVidia card do you have ?

---

### Post by Yezinki on 2008-08-10
4 GB......T7200......Nvidia Ge Force 7900GS 256 MB.

---

### Post by Sycron on 2008-08-10
Your nVidia GPU is suported. Here you can install the drivers. [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

---

### Post by dexter.deepak on 2008-08-10
i dont know at which step of install you are in trouble, but this is how you can do it easily, (i suppose you have already installed vista/xp)
at the partition stage, you will probably have windows on /dev/sda1.leave it alone.

1. select the partition you have chosen to install ubuntu, and delete it . you can also merge multiple partitions by deleting them, if you feel a need of more space for ubuntu

2. from the deleted space, you can make new partitions  "atleast 2" - / (called root) and swap

3.after you get free space after deleting , select "edit" ;
 then check the "logical drive" box.
 now in the filesystem type, specify "swap" and give it a size ,atleast  your ram size...maximum 1.5 times your ram , if you want you can use more.
 but i dont think thats of any use

4. again edit the leftover free space, and give it a size whatever you like to, at the mountpoint type "/" (without quotes). select the filesystem to be ext3. remember to make it logical drive.

5. if you have still some space left, you can create new partitions of any filesystem and mount them at some mountpoint like /media/disk_name

i think this should help you.

---

### Post by Yezinki on 2008-08-10
Being in Ubuntu how can I see the drive distribution/partitions?

---

### Post by Sycron on 2008-08-10
You can use gparted.

install it:
```
sudo apt-get install gparted
```and then run it
```
sudo gparted
```Hope this helps.

---

### Post by Yezinki on 2008-08-10
I installed/dual booted as per WRDN instrauctions.

Every thing is great except both OSs have slowed......Vista once gave a message low in resources.

Once again how can I see the partitions staying in Ubuntu.....so I can send ya guys a screen shot.

Plus the OSs are really dragging.

But No errors on display?

---

### Post by Sycron on 2008-08-10
You can use gparted.

install it:
```
$ sudo apt-get install gparted
```and then run it
```
$ sudo gparted
```Hope this helps.

---

### Post by Ihaveaproblem on 2008-08-10
Hi to all, I received a spam private message from a new user > motlanthoi.
I deleted the message but I'd like to inform the administrator about that. How I can do?
Thank you

---

### Post by Yezinki on 2008-08-10
ubuntu2@ubuntu2-laptop:~$ sudo apt-get install gparted
[sudo] password for ubuntu2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
ubuntu2@ubuntu2-laptop:~$ sudo gparted
sudo: gparted: command not found
ubuntu2@ubuntu2-laptop:~$ nauman
bash: nauman: command not found
ubuntu2@ubuntu2-laptop:~$

---

### Post by Sycron on 2008-08-10
You have to do this first: [http://www.ubuntux.org/node/71](http://www.ubuntux.org/node/71)

---

### Post by dexter.deepak on 2008-08-10
@OP
i wonder if you hav installed ubuntu or trying to install it ?

---

### Post by lukjad on 2008-08-10
I found an intersting link on how to dual/triple boot Ubuntu, XP and Vista. Here it is:

[http://thevistaforums.com/index.php?showtopic=19902](http://thevistaforums.com/index.php?showtopic=19902)

---

### Post by Yezinki on 2008-08-10
I have already installed a dual boot of Ubuntu & Vista.

On Sony Vaio VGC-LS!.......Ubuntu alone was great.

But on Dell XPS 1710 though twice the hardware its dragging.

How do I see the partitions??

---

### Post by Yezinki on 2008-08-10
For your views!

---

### Post by Sycron on 2008-08-10
Download [this](http://packages.ubuntu.com/hardy/i386/gparted/download), and run it by typing into a console:
```
$ sudo gparted
```

---

### Post by dexter.deepak on 2008-08-10
> **Yezinki said:**
> I have already installed a dual boot of Ubuntu & Vista.

On Sony Vaio VGC-LS!.......Ubuntu alone was great.

But on Dell XPS 1710 though twice the hardware its dragging.

How do I see the partitions??

you just need to see the partitions, or edit them too ??
for "seeing" them, look into the system-monitor
for editing them, install gparted :
```
sudo apt-get install gparted
```
remember to unmount any drive before editing it.

---

### Post by Sycron on 2008-08-10
> sudo apt-get install gparted
He can't do that since don't have the universe repositories. I told him to follow  this [http://www.ubuntux.org/node/71](http://www.ubuntux.org/node/71) but he didn't do that so i suggested him to download the deb directly from here [http://packages.ubuntu.com/hardy/i386/gparted/download](http://packages.ubuntu.com/hardy/i386/gparted/download).

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> For your views!

For one thing, you need to turn swap on, and why did you make it 7.8Gb (that's far far far too big)?

To turn swap on, use the command:

```
sudo swapon -a
```

---

### Post by vjkeito on 2008-08-10
this post seem to be bouncing around a bit!

please read the details I posted before about partitioning during setup, it sounds like you may have set it up wrong, perhaps leaving too little space for vista (hence the complaints regarding resources).

to view information about the current partitions and how they are setup you need to install and run gparted

**UPDATE**
```
sudo apt-get update
```
**INSTALL**
```
sudo apt-get install gparted
```
**RUN**
```
gksudo gparted
```

when running you should have *something that looks similar* to this

[IMG]http://img397.imageshack.us/img397/6623/screenshotdevsdagpartedhd8.png[/IMG]

---

### Post by dexter.deepak on 2008-08-10
> **Sycron said:**
> He can't do that since don't have the universe repositories. I told him to follow  this [http://www.ubuntux.org/node/71](http://www.ubuntux.org/node/71) but he didn't do that so i suggested him to download the deb directly from here [http://packages.ubuntu.com/hardy/i386/gparted/download](http://packages.ubuntu.com/hardy/i386/gparted/download).

ok i get it,
the OP should do this :
```
sudo gedit /etc/apt/sources.list
```
in the file that opens, uncomment (remove # in front of the lines) all the repositories :
```
## Major bug fix updates produced after the final release of the
## distribution.
#deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
#deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
```
to :
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
```

do the same with all repositories.

---

### Post by dexter.deepak on 2008-08-10
..and yes, after this :
```
sudo apt-get update
```

---

### Post by vjkeito on 2008-08-10
if you had read the information I gave you, you'd have known that 7.9GB for a swap is too big ;0)

always thoroughly read and understand something before going ahead and doing it.  there are, for instance, some people in the past who have told people to carry out certain commands on this forum (those which would damage the system) and blindly carrying those commands out without understanding (or taking the time to do so) may result in unsatisfactory results.

---

### Post by dexter.deepak on 2008-08-10
> **vjkeito said:**
> if you had read the information I gave you, you'd have known that 7.9GB for a swap is too big ;0)



yes this is too big a size indeed !!
i think i recommended you to give a maximum of 1.5 times your ram to the swap . i had only told you (not in order to be implemented, just for knowing) that we can have as big a swap as we like to have.

---

### Post by Yezinki on 2008-08-10
Your Views!!

---

### Post by vjkeito on 2008-08-10
my screenshot... (again)

you'll notice my "/home" isn't there.  that is because I haven't gotten round to putting my home folder on a separate partition (yet).  Putting your home folder on a separate partition is a good idea though.  it means when/if you reformat or install a new version of linux you can keep your home partition and all its data and choose to mount that partition with the new OS

---

### Post by vjkeito on 2008-08-10
also from what I've heard putting your swap last is also a very good idea.

---

### Post by Yezinki on 2008-08-10
Are my partitions wrongly made?

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> Are my partitions wrongly made?

The partition layout is fine, though I am curious as to why you used the [older] ext2 file-system for / and /home?

---

### Post by Yezinki on 2008-08-10
What should have I used?

Can I change em now?

Thanks!

---

### Post by Sycron on 2008-08-10
It is not older. Ext2 is Ext3 without journaling. Read more here [http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

### Post by Yezinki on 2008-08-10
How do I place a copy of Ubuntu on the 2nd logical partition?

---

### Post by Yezinki on 2008-08-10
Can I change it to ext3 now?

---

### Post by Sycron on 2008-08-10
type the output of
```
$ sudo fdisk -l
``` and i'll tell you how. all data on the 2nd logical partition will be lost.

---

### Post by Sycron on 2008-08-10
> Can I change it to ext3 now?
Why would you do it? You wont need it. It will 'kill' your HDD. :|

---

### Post by Yezinki on 2008-08-10
ubuntu2@ubuntu2-laptop:~$ sudo fdisk -l
[sudo] password for ubuntu2: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28aed868

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865       12161    58613152+   5  Extended
/dev/sda5            4865        5884     8193118+  82  Linux swap / Solaris
/dev/sda6            5885        9708    30716248+  83  Linux
/dev/sda7            9709       12161    19703691   83  Linux
ubuntu2@ubuntu2-laptop:~$ 
ubuntu2@ubuntu2-laptop:~$

---

### Post by Sycron on 2008-08-10
You can't do this as I can see the fdisk output. I suggest you reinstall ubuntu with the followings settings. 512MB swap , and one **/** (root) partition formated as ext2. But you can do everything you want with your computer ;).

---

### Post by Sycron on 2008-08-10
Do you have important data on ntfs partition ?

---

### Post by Yezinki on 2008-08-10
No

---

### Post by Sycron on 2008-08-10
Then do a reinstall of ubuntu with the following settings. 512MB swap , one **ext2** root partition of 10GB (Ubuntu uses only**3.5GB** so you wont need to store more than 6.5GB on home folder). The other partition could be a ntfs one but if you wont use Windows you can make it ext2 too.If you'll have problems feel free to ask on forums.

**[COLOR="Red"]Everything that is on HDD will be LOST!!!![/COLOR]**

---

### Post by WRDN on 2008-08-10
> **Sycron said:**
> Then do a reinstall of ubuntu with the following settings. 512MB swap , one **ext2** root partition of 10GB (Ubuntu uses only**3.5GB** so you wont need to store more than 6.5GB on home folder). The other partition could be a ntfs one but if you wont use Windows you can make it ext2 too.If you'll have problems feel free to ask on forums.

**[COLOR="Red"]Everything that is on HDD will be LOST!!!![/COLOR]**

The [FS- Driver]("http://www.fs-driver.org/") can be used to access ext2/3 partitions from Windows, and, as there is much less fragmentation than NTFS, I would recommend this setup for Yezinki.

---

### Post by Sycron on 2008-08-10
> **WRDN said:**
> The [FS- Driver]("http://www.fs-driver.org/") can be used to access ext2/3 partitions from Windows, and, as there is much less fragmentation than NTFS, I would recommend this setup for Yezinki.

I almost forgot about fs-driver :).

---

### Post by Yezinki on 2008-08-10
Okay.......previously the sawp was 2X RAM = 8 GB.

1 Extended partition......in which 3 logical partitions........1 for swap( 512 MB)......2nd for Ubuntu Install (30 GB).....3rd to save a copy of Ubuntu Hardy (...GB??)...yea?

---

### Post by Yezinki on 2008-08-10
Whats a FS driver??

Do newer versions of Ubuntu are released very frequently?

How shall I place a copy of Ubuntu on 3rd partition?

Why doesnt GParte appear on the menu always?

---

### Post by Yezinki on 2008-08-10
When I did a reboot & went into Vista it only showed 1 partition ie C drive?

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> When I did a reboot & went into Vista it only showed 1 partition ie C drive?

The FS-Driver is used to read/ write to ext2 and ext3 partitions. Windows cannot natively read/ write to the file systems, so you need to use the driver to access them.

---

### Post by Yezinki on 2008-08-10
What type of partitions should I have in the Extended........swap, ext2 OR 3 in the 2nd for Ubuntu install....size 10 GB......3rd for storing a copy.....Ext 2 or 3??

---

### Post by Sycron on 2008-08-10
I don't know why are you making a backup of your ubuntu instalation ? You can do this backup to a file. BUT the file would have the size of the partition. I mean if you install ubuntu on a 60GB partition then the backup file would have 60GB ... and since 120GB > 100GB you can't backup your system.

I suggest you to make a 5GB root partition where you'll install ubuntu and another partition where you'll be able to keep your data,documents,backups,music, etc. AND IF SOMETHING GOES WRONG then reinstall ubuntu on that 5GB partition.

---

### Post by vjkeito on 2008-08-10
I'm surprised most of you recommend the ext2 fs over ext3 as I see journaling as a useful feature of a modern file-system.  ext3 is stable and not too bad in terms of speed/performance.  there are other more notably faster alternatives, like ReiserFS (although how long ReiserFS will remain viable given the recent events regarding Hans Reiser - its main developer is unknown).

**[COLOR="SeaGreen"][FONT="Arial Black"]Yezinki please READ THESE articles [[[B]1**]("http://www.herman.linuxmaniac.net/p23.html")] [**[2]("http://www.psychocats.net/ubuntu/partitioning")**] NOW and gain a better understanding of what it is you are trying to achieve![/FONT][/COLOR][/B]

---

### Post by WRDN on 2008-08-10
> **Sycron said:**
> I suggest you to make a 5GB root partition where you'll install ubuntu and another partition where you'll be able to keep your data,documents,backups,music, etc. AND IF SOMETHING GOES WRONG then reinstall ubuntu on that 5GB partition.

5Gb seems very small if you are only using a root (/) and home (/home) partition (plus swap). While it is sufficient for the default installation, it may be too small if Yezinki wants to install multiple programs etc. I would recommend at least 10Gb for the root partition.

---

### Post by Yezinki on 2008-08-10
Gparte in Menu???

How does one access partitions with out the command for gparte?

512 MB for swap + 10 GB for Ubuntu install + 5 GB to place a copy & the rest for Vista??

Where is the FS driver installed?

Ext2 or Ext 3 is recommended?

How to place a copy of Ubuntu?

---

### Post by vjkeito on 2008-08-10
when using the FS driver in windows to access ext2/3 File-Systems, please read the manual!  be sure to dismount them properly using the IFS control panel entry.

---

### Post by Yezinki on 2008-08-10
Sycron

WRDN suggested to keep a partition to store a copy of Ubuntu?

---

### Post by Sycron on 2008-08-10
> **Ext2 or Ext 3 is recommended?** Ext2 is Ext3 without journaling.

---

### Post by vjkeito on 2008-08-10
> **Yezinki said:**
> Where is the FS driver installed?
in windows vista.  you have to [install it yourself]("http://www.fs-driver.org/").

> **Yezinki said:**
> Ext2 or Ext 3 is recommended?
I would use ext3 but as you can see people file-system of choice differs, use what you deem to be best for your needs.

---

### Post by Sycron on 2008-08-10
I don't know but you can make everything you want with your computer. I **personally** don't recommend to backup Ubuntu only on extremly rare cases. and I **personally** recommend using ext2 or ReiserFS. You wont need ext3.

---

### Post by Yezinki on 2008-08-10
So lets make a net summary for Vista & Ubuntu on 100 GB?

Would you care to explain in detail coz I have an image of Vista taken using Acronis true image.....just need to format & restore the image ......than I can start working to install Ubuntu.

---

### Post by WRDN on 2008-08-10
> **Yezinki said:**
> Sycron

**WRDN suggested to keep a partition to store a copy of Ubuntu?**

Did I?
I suggested you create 3 partitions: root (/), /home and swap.

---

### Post by Sycron on 2008-08-10
I think i'll retire from this thread. I'm gonna have headaches :| .

---

### Post by Yezinki on 2008-08-10
Ext 2 is pretty slow.

---

### Post by Sycron on 2008-08-10
> Ext 2 is pretty slow. 
Then get ReiserFS.

---

### Post by Yezinki on 2008-08-10
I am sorry WRDN.....may be too much for a day.....i thought you did but am wrong for which I apologize.

---

### Post by Yezinki on 2008-08-10
Thanks Sycron & WRDN...........I appreciate your patience......have a great evening/day!

---

### Post by Sycron on 2008-08-10
Read here: [http://www.planetmy.com/blog/linux-file-sytem-ext2-and-ext3/](http://www.planetmy.com/blog/linux-file-sytem-ext2-and-ext3/) and you'll know what is for you.

---

### Post by vjkeito on 2008-08-10
you still appear to be confused.

I myself will no longer be posting to this thread after this.

I have said it many times already.

GO BACK and READ ALL MY REPLIES AND LOOK/READ THE RELATED ARTICLES THAT I HAVE LINKED TO.

These will tell you exactly what to do.  By ignoring this advice you will only find yourself going round in circles.  Please learn to take the advice and you will learn Ubuntu & Linux practices far faster, instead of wasting whole days on something which could have been rectified far sooner.

That is all I am going to say, take it or leave it.

Good Luck!

Regards,
Keito

---

### Post by Sycron on 2008-08-10
Yezinki you have to do what vijkeyto told you. Read [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/) , especially [http://www.funnestra.org/ubuntu/hardy/#install](http://www.funnestra.org/ubuntu/hardy/#install) . **It would probably be better not to rush**.

---

### Post by vjkeito on 2008-08-10
> **Sycron said:**
> Yezinki you have to do what vijkeyto told you. Read [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/) , especially [http://www.funnestra.org/ubuntu/hardy/#install](http://www.funnestra.org/ubuntu/hardy/#install) . NEVER Don't rush.

that particular guide if read initially would have covered many of your questions (partitions, filesystems, etc) and perhaps nipped any confusion you had in the bud, about what relates to what, early on.

---

### Post by WRDN on 2008-08-10
> **Sycron said:**
> Yezinki you have to do what vijkeyto told you. Read [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/) , especially [http://www.funnestra.org/ubuntu/hardy/#install](http://www.funnestra.org/ubuntu/hardy/#install) . **NEVER Don't rush**.

It would probably be better not to rush ;)

---

### Post by Sycron on 2008-08-10
> **WRDN said:**
> It would probably be better not to rush ;)

OK, sorry for my English....

---

