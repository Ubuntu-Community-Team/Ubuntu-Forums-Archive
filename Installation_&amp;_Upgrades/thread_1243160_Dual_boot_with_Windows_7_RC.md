---
title: "Dual boot with Windows 7 RC"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by cob on 2009-08-18
I can't seem to find a guide to booting Windows 7 from GRUB after installing Ubuntu.  This would be after installing Windows 7 first.  I haven't tried yet, but since there seems to be a lack of knowledge on this subject.  I would be willing to use my laptop as a guinea pig for any attempts, since it doesn't have any data I care about on it yet.

That is, unless someone has a reliable method already?  Google hasn't been kind to me on this.

---

### Post by louieb on 2009-08-18
Win 7 can be chainloaded from GRUB just like Vista and XP. Any guide that work for one of those should work for Win 7 too. [apc HowTo dual boot]("http://apcmag.com/howto_category.htm?cid=198")

---

### Post by stinger30au on 2009-08-18
i tried a spare hdd today with win 7 rc1 & 9.04

install win 7 first

then boot 9.04

when the first boot screen comes up hit install ubuntu

work u way thru the install setps till it shows you the hdd install page

up top it says hdd has vista on it and there is a green bar that goes from left to right

down the bottom is another bar
theres a slider on the lower bar in the right corner, click and drag on it and give ubuntu some space to use

i tried it on a 320 gig hdd and gave 9.04 100 gig and it rns fine dual boot

to make life easier install windows first

if not then super grub disk make it a lot easier

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by cob on 2009-08-18
Well, it seems to be different between Vista and Win 7.  Here is what happens during partitioning with an existing Win 7 partition.  It doesn't recognize my Win 7 partition properly, and if I use the largest contiguous free space, it tries to only use 2.5GB for Ubuntu.

[IMG]http://img194.imageshack.us/img194/9751/partitioner.png[/IMG]

---

### Post by presence1960 on 2009-08-18
> **cob said:**
> I can't seem to find a guide to booting Windows 7 from GRUB after installing Ubuntu.  This would be after installing Windows 7 first.  I haven't tried yet, but since there seems to be a lack of knowledge on this subject.  I would be willing to use my laptop as a guinea pig for any attempts, since it doesn't have any data I care about on it yet.

That is, unless someone has a reliable method already?  Google hasn't been kind to me on this.

So you have Win 7 & Ubuntu installed? then boot from Ubuntu and use the link in my signature line to download the Boot Info Script 0.32 to desktop. Once on the desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of this file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text. This info will show us your setup and boot process.

---

### Post by cob on 2009-08-18
Actually I don't have Ubuntu installed yet; I installed Windows 7 first, and now want to put Ubuntu in the free space on the other half of my drive.

---

### Post by presence1960 on 2009-08-18
you have two options then. Use install them side by side by clicking next and at the next window you will have a graphic of your windows partition. use the mouse to drag the right end of the windows partition to the left until you have the amount of space you want for Ubuntu.

or you can use the manual option to create partitions for ubuntu. if you choose to use manual I suggest you post back to get some suggestions unless you are really familiar with partitioning.

---

### Post by cob on 2009-08-18
I'm worried that the install partitioner is going to waste my NTFS partition, because it recognizes it, but not as a Windows partition.  It doesn't seem to understand how much free space is available, because if I tell it to use the largest contiguous free space, it only attempts to use 2.5GB rather than the available 116.7GB.  If I use the slider, it would allow me to use more than 116.7GB.  Rather than showing up as a blue "Windows Vista" partition, it shows the green /dev/sda2 with no file system specified.

---

### Post by stinger30au on 2009-08-19
do u want the windows and ubuntu on the same hard drive or ubuntu on second hard drive.

theres a few ways to attack getting ubuntu and windows on to the first hdd

i have mentioned one way previously

the other way is to *manually* create a free space section on the first hdd for ubuntu to install too

theres a number of tutorials on how to do it but a quick run down is this

install windows to the pc first and make sure it running nicely

then boot up off ubuntu cd and select - runu ubuntu with no changes to pc

when ubuntu starts click on system , administration, gparted - or partition editor

select the hdd that has windows installed and move the slider to the right and make some free space


let gparted do its thing

then run the installer and tell ubuntu to use largest free space and it will do its thing

---

### Post by presence1960 on 2009-08-19
> **stinger30au said:**
> 

theres a number of tutorials on how to do it but a quick run down is this

install windows to the pc first and make sure it running nicely

then boot up off ubuntu cd and select - runu ubuntu with no changes to pc

when ubuntu starts click on system , administration, gparted - or partition editor

select the hdd that has windows installed and move the slider to the right and make some free space


let gparted do its thing

then run the installer and tell ubuntu to use largest free space and it will do its thing

I would be very wary of using gparted to shrink a vista partition. it may or may not work. While some have done it successfully, it is a documented fact that a lot of users who used gparted to alter their vista partition wound up with vista being unbootable among other problems. I would recommend shrinking vista's partition to create free space for ubuntu with vista's disk management utility.

OP: There are no guarantees in any OS install or partitioning operation. Anything can happen at any time unexpectedly. That is why you are strongly suggested to back up your data before doing these operations. There are software that will make an image of your windows partition if you want or just simply back up files. When you jump out of a plane it is suggested that you pull the ripcord! It is suggested you back up your data prior to doing this. As for guarantees no one can make them for you. 

I would shrink Vista's partition using Vista's disk management utility. Then boot the ubuntu live CD choose "try ubuntu without any changes", when the desktop loads open a terminal and run > gksu gparted and use gparted to create a ext3 or ext 4 partition for Ubuntu and a swap partition. Then install using the manual option.

I think maybe you should do some reading to become familiar with what you are going to do:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) -shows how to use vista's disk management utility to shrink vista partition
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/) for a free pdf ubuntu pocket guide which BTW has a great step by step on the install process
[https://help.ubuntu.com/9.04/switching/first-steps.html](https://help.ubuntu.com/9.04/switching/first-steps.html)

---

### Post by cob on 2009-08-19
> **presence1960 said:**
> OP: There are no guarantees in any OS install or partitioning operation. Anything can happen at any time unexpectedly. That is why you are strongly suggested to back up your data before doing these operations. There are software that will make an image of your windows partition if you want or just simply back up files. When you jump out of a plane it is suggested that you pull the ripcord! It is suggested you back up your data prior to doing this. As for guarantees no one can make them for you. 

Well, obviously.  I've never had trouble with Ubuntu installations in another area of free space on a drive with XP, but this is looking wholly different.  Again, I'm nervous since the partitioning portion of the installer does not seem to respect the dimensions of the /dev/sda2 partition (which is actually my Win 7 NTFS partition); why should I believe it isn't going to overwrite it, or damage the partition table irrevocably?  I understand people have done this with Vista, and that Windows 7 is only slightly different, but this is definitely not expected, and seems to be different from the results others get with an NTFS partition with Vista installed.

> I would shrink Vista's partition using Vista's disk management utility.

I already have the free space available, since I planned this from the beginning.

> Then boot the ubuntu live CD choose "try ubuntu without any changes", when the desktop loads open a terminal and run  and use gparted to create a ext3 or ext 4 partition for Ubuntu and a swap partition. Then install using the manual option.

I'll give it a shot, I guess.  I'm not worried about losing any data right now since the Win 7 install is relatively new.

> I think maybe you should do some reading to become familiar with what you are going to do:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) -shows how to use vista's disk management utility to shrink vista partition
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/) for a free pdf ubuntu pocket guide which BTW has a great step by step on the install process
[https://help.ubuntu.com/9.04/switching/first-steps.html](https://help.ubuntu.com/9.04/switching/first-steps.html)

I am pretty familiar with partitioning and bootloading via GRUB and the old NTLDR; appears GRUB will simply chainload the new Win 7 bootloader.

I'll come back here once I've tried it with my results.  I'll try just using the graphical installer first, then a manual partitioning method.

---

### Post by presence1960 on 2009-08-19
> **cob said:**
> 

I am pretty familiar with partitioning and bootloading via GRUB and the old NTLDR; appears GRUB will simply chainload the new Win 7 bootloader.

I'll come back here once I've tried it with my results.  I'll try just using the graphical installer first, then a manual partitioning method.

Sorry if that came off the wrong way but I have no idea how experienced you are. I usually suggest some reading for inexperienced members when it comes to partitioning and installation.

Creating partitions before the install and using the manual option will eliminate the risk of what you are afraid of happening. Using manual will not touch sda2, only the partitions you specify in the manual operation.

---

### Post by louieb on 2009-08-19
As your finding out the partition stage of Ubiquity is still a little flaky.   All I know is that before putting Win 7 on my desktop, the partitions were already set up.  I did a custom install of Win 7 - told it to format and install in sda2.  After the install used a live CD to put GRUBs stage1 code back in the MBR. and added a WIN 7 chain-load entry to menu.lst.

Since my partitions were setup in advance could have just a easily installed Win 7 then installed Linux.

One thing I've been seeing is a lot of Grub error 18 threads. Might want to partition so that both OS install in the first 137 GB of the disk.  What I do is set up partitions in the 1st part of the drive for the OS(s)  and create partition for data  in the remainder of the drive.

---

### Post by presence1960 on 2009-08-19
> **louieb said:**
> 



One thing I've been seeing is a lot of Grub error 18 threads. Might want to partition so that both OS install in the 137 GB of the disk.  What I do is set up partitions in the 1st part of the drive for the OS(s)  and create partition for data  in the remainder of the drive.

+1

Those with older machines need to be aware that their BIOS may not be able to read past a certain point on their hard disks and as you said should create their partitions for OSs within that boundary.

---

### Post by cob on 2009-08-20
Well, I manually partitioned with gparted, and I'm able to boot both OSes fine.

---

### Post by presence1960 on 2009-08-20
> **cob said:**
> Well, I manually partitioned with gparted, and I'm able to boot both OSes fine.

excellent!! Enjoy!

---

### Post by Herman on 2009-08-20
I don't believe there is actually any documented instances of GParted in Ubuntu's installer doing damage to Vista's boot sector. I spent a lot of my time reading through all the bug reports I could find in Launchpad last time this subject came up.
I also spent a lot of my own time installing Windows 7 and Ubuntu, and Vista and Ubuntu, and I was not able to reproduce any problem.
This time I didn't have time for an exhaustive search, but I didn't see any bugs reported about GParted in Ubuntu making Windows Vista or Windows 7 unbootable.

Windows Vista and Windows 7 have departed from tradition and no longer have their partition starting in sector 63, after the first track of the hard disk. Instead, their first sectors start in number 2048, I don't know why. Perhaps is has something to do with an expected increase in the popularity of SSD drives. The flash memory in SSD drives is erased a block at a time, and is is thought that having the partition starting at the start of an erase block will help the performance and reduce wear in flash memory drives. I'm only guessing about that though, there might be some other reason for Microsoft suddenly departing from convention and switching to sector 2048. 

It is possible to accidentally allow GParted to move the Windows partition if we use GParted in the Ubuntu Live CD or some other version of GParted as a program by itself, but not in the Ubuntu installer. 
GParted has a check box to let the user decide whether partitions should be aligned on cylinder boundaries. Users of Windows 7 and Windows Vista should be careful to remove that checkmark before working on their Windows partition in GParted. However, no real harm will be done even if the user doesn't know or if they forget to remove the checlmark because GParted in Ubuntu will run the program for updating the Windows boot sector, which Ubuntu does have. 
GParted in the Ubuntu installer doesn't have such a checkbox, because the Ubuntu installer doesn't move the Windows partition in any case, so the Ubuntu installer is quite safe.
I deliberately did my worst to my test installations of both Vista and Windows 7 repeatedly, using GFParted in Ubuntu separately from the installer, and on all occasions, much to Microsoft's credit, the boot loader was always able to repair itself automatically after a short wait. On most occasions I needed to use the installation CD, but it was always easy to repair.

There was a bug in GParted Live CD quite some time back which had nothing at all to do with GParted in Ubuntu. Apparently the GParted LiveCD was made with a small program omitted which was for updating the Windows boot sector if the start of the Windows partition is moved.
It seems to me that's the likely origin of these ongoing complains about GParted, but it has never had anything to do with Ubuntu's GParted, only GParted in GParted LiveCD, which is a different distro from Ubuntu.

There's probably no harm in advising people to use Windows Vista or Windows 7's partitioner, and err on the side of safety.
However, on the other hand, the problem in GParted Live CD has already been solved long ago, and this problem has never been a Ubuntu problem at all. I don't think there is any real need to keep repeating warnings in Ubuntu Web Forums about a problem that existed in an obsolete version of some other distro.

---

### Post by cob on 2009-08-20
Herman,

gparted didn't give me any problems, and recognized (and reported) the Win 7 partition correctly in size and in NTFS format.  The only problem was that the Ubuntu installer wasn't recogizing (or reporting) on that partition correctly.  It would also allow me to make a larger ext3 partition for Ubuntu than there was available free space on the drive for, which led me to believe that it was not going to respect the NTFS partition and destroy it, or at best, resize it.

I've seen screenshots of the 9.04 installer reporting on Vista NTFS partitions correctly, and didn't think there was much difference between the Vista and Win 7 partitioner, and since both are NTFS filesystems, you'd think this wouldn't have been an issue.

I'll submit a bug against it.

---

### Post by Herman on 2009-08-20
Okay.  it does seem like something the developers might be interested in taking a closer look at,  possibly a bug either in Windows 7 or in Ubuntu's installer. 

originally posted by [presence1960]("http://ubuntuforums.org/member.php?u=657448"),
> I would be very wary of using gparted to shrink a vista partition. it may or may not work. While some have done it successfully, **it is a documented fact that a lot of users who used gparted to alter their vista partition wound up with vista being unbootable among other problems**. I would recommend shrinking vista's partition to create free space for ubuntu with vista's disk management utility. Can anyone provide links to these documents? It looks like I'm going to  be spending a lot of my spare time  searching through Launchpad for bug reports again for any documented case of GParted messing up people's partition tables after Windows Vista or Windows 7 have been installed.  I'll need to update my website rather urgently if that's true as I recommend using GParted in Ubuntu to resize the Windows partition and I don't want to be giving people the wrong information.

---

### Post by presence1960 on 2009-08-20
Herman,

[http://bugzilla.gnome.org/show_bug.cgi?id=379482](http://bugzilla.gnome.org/show_bug.cgi?id=379482)

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Plus the very numerous threads in here from those who used gparted live cd or gparted from the Ubuntu installer to shrink vista and create space for ubuntu.

There have been so many instances of posts pertaining to this that along with numerous other forum members I have been recommending using Vista's disk management utility to shrink Vista's partition to make room for Linux installations.

Gparted plays very nicely with XP and w2k.

---

### Post by Herman on 2009-08-20
Thanks, presence1960, I'm reading those now ... :-k

---

### Post by presence1960 on 2009-08-20
> **Herman said:**
> Thanks, presence1960, I'm reading those now ... :-k

BTW your site contains a lot of useful info. I like it.

---

### Post by Herman on 2009-08-20
:) Okay, and thanks for all the help you're giving Ubuntu users here in Ubuntu Web Forums too, presence1960, you and without people like you help to make Ubuntu Web Forums great!

The links you posted are about GParted Live CD though, not GParted in Ubuntu, so although the information in them may have been correct at one time for certain old versions of GParted Live CD, it probably doesn't apply to GParted in Ubuntu, especially not recent versions of Ubuntu anyway.

I wish the how-to geek would update his web page and try using a newer version of GParted Live CD. Then he or she could show people the right way to resize a Vista or Windows 7 partition with GParted, by removing the check mark from the 'align to cylinders' checkbox. ](*,)

The problem I thought you were refering to was a slightly more serious problem,          [**Bug 574389** -       ]("http://bugzilla.gnome.org/show_bug.cgi?id=574389")        [No /usr/bin/xxd file]("http://bugzilla.gnome.org/show_bug.cgi?id=574389"), which as far as I know was limited to one or two out of date editions of GParted Live CD only, made before 2nd April 2009. This bug would never have applied to GParted in Ubuntu, since the xxd file is part of vim-common, which is or was included in Ubuntu. Here's a link to the previous thread where I went through a lot of work before I found out what that problem was, [Is Partition Magic Reliable?]("http://ubuntuforums.org/showthread.php?t=1107391&page=7") - Ubuntu Web Forums.
GParted doesn't depend on xdd any more, [[gparted] Remove requirement for xxd and dd for NTFS move or paste action: msg#04381]("http://osdir.com/ml/svn-commits-list/2009-05/msg04381.html").

GParted in the Ubuntu installer wouldn't have had that problem anyway, even if it didn't have xxd, because the Ubuntu installer doesn't move the start of the existing partition. It's impossible to get the Ubuntu installer to do that so it shouldn't cause anyone any problems.
It is possible to get GParted in the Ubuntu Live CD or some other GParted to move the Windows partition, and then it would mean inconvenience for the Vista or Windows 7 user because they would need their Vista or Windows 7 CD to fix their boot loader, but only if they don't remove the tick from the 'round to cylinders' checkbox in modern versions of GParted.

Points in favor of using Windows 7 or Vista's partitioner are for one, if the partition table does get borked, it wouldn't be Ubuntu's fault. Secondly, and more importantly for some, the Windows 7 / Vista partitioner makes the start for the first partition at sector 2048 by default.  That's ideal for users installing in some kinds of SSD drives or flash memory sticks. To do that in Ubuntu we need to use a CLI paritioner like fdisk, which is not so simple for new users.
I haven't decided whether that's important or not, since SSD manufacturers might decide to change their flash controllers in a way that makes them emulate a hard disk better, so then no changes will need to be made to disk partitioning. We'll have to wait and see what happens.

Regards, Herman :)

---

### Post by presence1960 on 2009-08-20
Thanks Herman. I am going to take some time and digest all this. This has been an ongoing point of contention in the forum. I for one only care about the truth and I am not shy about bucking popular opinion if it is false. I am one of the more vocal ones who take on the myth that windows **_must_** be installed before linux. Undoubtedly it is more convenient to do it that way, but what  if a person already has Ubuntu installed and wants windows? or their windows dies and have to reinstall it? Popular opinion is to remove the Ubuntu install, put windows on first then reinstall ubuntu. That is a lot of unnecessary work when all you need to do in most cases is just restore GRUB to MBR. I know I am rambling, but I get fired up about things like this because some would have these people remove a perfectly good OS and then install 2 OSs when all they had to do was install windows and restore GRUB. I am at a loss where that myth that windows must be installed before ubuntu came from, but it is not true.

Anyway, I have a lot to digest here so as soon as I can I will begin. Thanks again Herman.

---

### Post by Herman on 2009-08-20
[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]
Here's an image to show the 'Round to cylinders' checkbox.
This is what is not shown in the how-to geek's site.
If people would remove the checkmark from that checkbox before resizing their Windows 7 or Vista partition then GParted will leave the start point of that partition at sector number 2048 instead of moving it to sector number 63.
That's what we should be telling people.
Then their partition resize would be faster and they would not need to go through the additional inconvenient procedures advised in the how-to geek's site.
That site is good for helping people after they have already made the mistake, but it's not helpful and may even be misleading for people who want to use up to date versions of GParted for resizing Windows.

There's no need to look for any checkbox to clear in the Ubuntu installer's partitioner though, and it doesn't move the partition, so it's quite safe and has been all along. :)

---

### Post by majamba on 2009-08-20
let make it easier use the ubuntu live cd 

go to partinono editor create 2 partions -make the first fat32
make 2 partions 
1. Fat 32
2. Ext3 or Ext4(the linux partion)

restart after that
install first win 7

after that boot again from ubuntu live cd
open the partion editor select flags-boot to the second partioon
then install ubuntu 
in step 4 or 5 in the installation in the advanced tab you can choose where to put the butloader hd0,1

---

### Post by presence1960 on 2009-08-20
> **Herman said:**
> [IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]
Here's an image to show the 'Round to cylinders' checkbox.
This is what is not shown in the how-to geek's site.
If people would remove the checkmark from that checkbox before resizing their Windows 7 or Vista partition then GParted will leave the start point of that partition at sector number 2048 instead of moving it to sector number 63.
That's what we should be telling people.
Then their partition resize would be faster and they would not need to go through the additional inconvenient procedures advised in the how-to geek's site.
That site is good for helping people after they have already made the mistake, but it's not helpful and may even be misleading for people who want to use up to date versions of GParted for resizing Windows.

There's no need to look for any checkbox to clear in the Ubuntu installer's partitioner though, and it doesn't move the partition, so it's quite safe and has been all along. :)

Herman, I have been going through what you have posted and it is starting to make sense. I want to study it a little longer as I am very much the analytical type. I appreciate you sharing this info and I have bookmarked this page for future reference.

---

### Post by gordintoronto on 2009-08-20
> **cob said:**
> 
I already have the free space available, since I planned this from the beginning.


I recently installed on a brand new hard drive.  I installed Windows 7 RC, telling it to use 60 GB.  Then I told Ubuntu to use 40 GB for root, 8 GB for swap and the rest for Home.  Worked perfectly.

---

### Post by raymondh on 2009-08-20
> **Herman said:**
> [IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]
Here's an image to show the 'Round to cylinders' checkbox.
This is what is not shown in the how-to geek's site.
If people would remove the checkmark from that checkbox before resizing their Windows 7 or Vista partition then GParted will leave the start point of that partition at sector number 2048 instead of moving it to sector number 63.
That's what we should be telling people.
Then their partition resize would be faster and they would not need to go through the additional inconvenient procedures advised in the how-to geek's site.
That site is good for helping people after they have already made the mistake, but it's not helpful and may even be misleading for people who want to use up to date versions of GParted for resizing Windows.

There's no need to look for any checkbox to clear in the Ubuntu installer's partitioner though, and it doesn't move the partition, so it's quite safe and has been all along. :)

Thanks Herman ... likewise bookmarked :)

---

### Post by cob on 2009-08-20
majamba, I don't think the OSS community should expect the average Windows user to go through all that trouble.  Ubuntu's installer is expected to perform this task without a great deal of effort, especially in such a straightforward case as mine, where the free space was already arranged on the disk.  As Windows 7 RTM becomes more ubiquitous, this is going to go from niche cases to mainstream problem for new users.

Sure, those of us who have used linux for years are going to be comfortable with manual partitioning methods, and know that we need not only our root ext3 partition, but a swap as well, but I wouldn't expect a "newbie" to have that kind of insight.

---

### Post by cob on 2009-08-20
> **gordintoronto said:**
> I recently installed on a brand new hard drive.  I installed Windows 7 RC, telling it to use 60 GB.  Then I told Ubuntu to use 40 GB for root, 8 GB for swap and the rest for Home.  Worked perfectly.

I'm using Windows 7 build 7100 (32-bit).  What are you using?  I wonder why there's disparity between our experiences with the partitioning step.  I don't suppose you would be willing to wipe your Ubuntu and swap partitions out and do it again, this time taking a screenshot? :)

---

### Post by presence1960 on 2009-08-20
> **presence1960 said:**
> Herman, I have been going through what you have posted and it is starting to make sense. I want to study it a little longer as I am very much the analytical type. I appreciate you sharing this info and I have bookmarked this page for future reference.
 Ok , I absorbed what you shared. I downloaded the latest stable version of gparted Live 0.4.5-2 and made a bootable USB. I booted into gparted Live and tried to resize my Win 7 partition unchecking the round to cylinder box. I kept getting an error. So I went to Info on the Gparted Live desktop and clicked on the Light Bulb. A menu came up and I choose windows information. I will attach a cropped pic of that screen which basically says Gparted is unable to resize Vista at this time. I did see on the latest unstable release they had a fix for NTFS in regards to xxd. Well anyways here is that shot, I cropped out the XP info because that isn't relevant and cut down the size so I could post it here.

---

### Post by Herman on 2009-08-21
Oh, okay, that is interesting information, and relevant too. I expect though, that there will be a difference between GParted Live CD and GParted in Ubuntu, GParted in Parted Magic and so on.  I have to admit though, it has been a while since I was testing this, only a few months, but ages in terms of software updates.
I hope GParted in Ubuntu will prove to be okay, it was the last time I tested, and I'm still optimistic at this stage that it will prove to be so. I will start re-testing myself in a few hours, I have some business to attend to first and then I'll start some tests.
Thanks for testing and sharing your information.

---

### Post by presence1960 on 2009-08-21
> **Herman said:**
> Oh, okay, that is interesting information, and relevant too. I expect though, that there will be a difference between GParted Live CD and GParted in Ubuntu, GParted in Parted Magic and so on.  I have to admit though, it has been a while since I was testing this, only a few months, but ages in terms of software updates.
I hope GParted in Ubuntu will prove to be okay, it was the last time I tested, and I'm still optimistic at this stage that it will prove to be so. I will start re-testing myself in a few hours, I have some business to attend to first and then I'll start some tests.
Thanks for testing and sharing your information.

No problem herman, I am very interested in this, as we have a lot of newer members wanting to dual boot with vista.

---

### Post by Herman on 2009-08-21
I have two tests completed now, I tried out GParted in Ubuntu Jaunty Jackalope 'Desktop' Live/Install CD, and then Parted Magic-4.2 Live CD 

Before I started, my Windows 7 separate /boot partition started in sector 2048 as expected. I verified that by right-clicking on the partition in GParted and clicking 'Properties'.
The last sector of mine is 411647 and the file system contained inside the partition is 33% used.

The first test was with GParted in Ubuntu Jaunty Jackalope Desktop Live CD.
I was easily able to choose 'resize the partition', and after removing the check mark from the 'round to cylinders' check box, I resized the partition to about half of its original size.
Then I rebooted and selected Windows 7 from my GRUB menu and Windows 7 booted right up as expected. Before booting was completed it ran a quick CHKDSK as it is supposed to do after a resize by GParted, that only took 3 or 4 seconds because it's a small file system and my Windows 7 booted up just fine and peachy!
To complete the test I rebooted Jaunty Jackalope and opened GParted again, removed the checkmark from the 'round to cylinders' checkbox again, and resized my Windows 7 /boot to fill the available free space again. 
Once again, Windows 7 booted, ran CHKDSK and proceeded to boot completely without and problem at all.

For the second test I repeated the same procedure with Parted Magic-4.2 Live CD with identical results.

I should also note that it could be important to watch that we don't accidentally 'move' the partition (with the four-headed arrow in Parted Magic), but only resize it, (using the two-headed arrow to resize the partition).

I was planning on running the same test again with GParted Live CD-0.3.4-7, but I had problems getting it to boot, it didn't like my keyboard. Every time it got to the keyboard selection I had no keyboard with which to select a keyboard with so I got stuck and had to press my computer's reset switch to reboot and try again. 
I'll give GParted Live CD one more try with a different version and see if that helps.

At the end of those two tests,  my Windows 7 separate /boot partition started in sector 2048 and the last sector of mine is 411647, exactly the same it it was before I started.

Regards, Herman :)

---

### Post by Herman on 2009-08-21
I have now completed a third test, resizing Windows 7 /boot partition with GParted LiveCD gparted-live-0.4.5-2.

I didn't have any keyboard problem booting gparted-live-0.4.5-2 in my computer and I used exactly the same procedure as already described with exactly the same results.

Maybe I'm just lucky, but so far I haven't run into any difficulties booting Windows 7 after resizing with GParted.

Regards, Herman :)

---

### Post by presence1960 on 2009-08-21
> **Herman said:**
> 

Maybe I'm just lucky, but so far I haven't run into any difficulties booting Windows 7 after resizing with GParted.

Regards, Herman :)

I couldn't resize my Win 7 partition with gparted Live, But I don't have a separate boot folder (system reserved) for win 7. I didn't get a chance yet to try this with the Ubuntu Live CD or Parted Magic 4.4.

I think it may be a matter of chance since the documentation from Gparted Live I posted says that sometimes it resizes the Vista partition & sometimes it doesn't. Anyway it is worth doing these experiments and sharing info because we have a lot of newer members and surely more to come who want to dual boot Vista with Ubuntu.

---

### Post by Herman on 2009-08-21
:) I have often found that when GParted will refuse to resize a partition which contains an NTFS file system all I need to do is boot a Windows CD and run CHKDSK and then try again with GParted.

---

### Post by gordintoronto on 2009-08-22
> **cob said:**
> I'm using Windows 7 build 7100 (32-bit).  What are you using?  I wonder why there's disparity between our experiences with the partitioning step.  I don't suppose you would be willing to wipe your Ubuntu and swap partitions out and do it again, this time taking a screenshot? :)

I'll pass on reinstalling.  Even though it went very smoothly, it still takes time to create the list of installed apps, then install them all, to export my email and Evolution settings and then import them, and copy over my data from the old (Ubuntu 7.10) hard drive, mounted in a USB enclosure.

I have the same build of Windows 7, but I installed the 64-bit version.  I actually installed Mint (Gloria), which is based on Ubuntu 9.04, also the 64-bit version.  My Linux partitions are EXT3.

I'm not sure what I would take a screen shot of.  The partitioning was all very straightforward.

---

### Post by Mark Phelps on 2009-08-22
> **presence1960 said:**
> I think it may be a matter of chance since the documentation from Gparted Live I posted says that sometimes it resizes the Vista partition & sometimes it doesn't. Anyway it is worth doing these experiments and sharing info because we have a lot of newer members and surely more to come who want to dual boot Vista with Ubuntu.

While it may be that GParted only rarely corrupts the Vista OS, statistics don't mean much when it's YOUR machine that got corrupted and you don't have a Vista DVD to use to fix it.

Which is why I have continued to advise folks, especially those with preinstalled Vista machine (who most probably do NOT possess a Vista DVD) to err on the side of caution and use the Vista Disk Management utility to shrink Vista.

Also, while the first indications are that Windows 7 is not subject to the same corruption problems, I don't think we've seen a large enough usage base to know that for sure yet.  But the initial results are a lot more promising than with Vista.

---

### Post by presence1960 on 2009-08-22
> **Mark Phelps said:**
> While it may be that GParted only rarely corrupts the Vista OS, statistics don't mean much when it's YOUR machine that got corrupted and you don't have a Vista DVD to use to fix it.

Which is why I have continued to advise folks, especially those with preinstalled Vista machine (who most probably do NOT possess a Vista DVD) to err on the side of caution and use the Vista Disk Management utility to shrink Vista.

Also, while the first indications are that Windows 7 is not subject to the same corruption problems, I don't think we've seen a large enough usage base to know that for sure yet.  But the initial results are a lot more promising than with Vista.

I here you Mark, that's why I have been one of those who staunchly advise to shrink Vista with it's own disk management utility. Until we have a definitive answer that yes like Ivory soap - 99.9% of partitioning with the Ubuntu live Cd or gparted live will successfully do the job with Vista I will still insist that those on here looking to dual boot with Vista stay away from using gparted either from the Ubuntu live cd or gparted live cd.

On the other hand I am really intrigued by herman's testing. I had done some myself and I posted the message from within gparted live cd  that is located in Info (light bulb on desktop) > windows information which clearly states that sometimes it works with Vista and sometimes it does not. if it were my machine I would not chance it, so I am not going to suggest that someone else chance it either.

---

### Post by Herman on 2009-08-22
Well if they don't have a Windows Vista DVD, how are they going to use Vista's partition editor to shrink their Vista partition then, I wonder?
Unless Vista has some way of shrinking its own partition while the operating system is mounted and running somehow, but that seems unlikely to me. Nevertheless, I'll give it a try. 
I found the How-To Geek's '[Resize a Partition for Free in Windows Vista]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")', and I'll try following those instructions and see what happens.

By the way, if anyone doesn't have a Vista or Windows 7 Installation disc and they want to use the repair tools, they can go and download one for free without the Vista installer in it. It looks like a real installation DVD and you can run the repair tools, but you can't install anything with it. It's free from NeoSmart.net, and it's only a small download,   [Windows Vista Recovery Disc.]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")
If you have one of those, you can use it for doing what the How-to Geek shows you in [Using GParted to Resize Your Windows Vista Partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/").

Anyway, I have no objection to the idea of people using Vista or Windows 7's partitioner for shrinking their Vista or Windows 7 partition.

Give GParted it's due respect though too, I believe *when it's used correctly* it will be more than 99.999% perfect to do the job of shrinking Windows7 and Vista partitions without any boot loader problems and if you do have a boot loader problem, it would mostly be easily fixed with your [Windows Vista Recovery Disc.]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")
A file system check is to be expected, it's normal and that doesn't indicate a corrupt file system, GParted induces that on purpose.

I have written to the How-to Geek to try to get that web page updated, it's an excellent web page for how to fix Vista. It could be even better if it showed how a recent version of GParted can be used and if people can be shown the right way to do things in the first place. Then they wouldn't really need to know how to fix it except if they made a mistake.

And I agree that, thankfully, Windows 7 does seem to be an improvement on Vista, I like their idea of having a separate /boot.

---

### Post by Herman on 2009-08-22
\\:D/ Wow!
I rebooted into Windows 7 and followed the How-to Geek's  [Using GParted to Resize Your Windows Vista Partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"), and it worked!
Not only it actually resized the /boot and the C: drive while it was still mounted and had a running operating system in it, it was quick too!

Okay, I have to agree that it's probably better to use Windows 7 or Vista for resizing Windows 7 or Vista partitions. I hate to admit it, but you win. :evil:

I still maintain the GParted can do it too though, especailly GParted in the Ubuntu installer, although you have to know how and it's not as fast.

---

### Post by presence1960 on 2009-08-22
It is not about winning or losing ( I know you know that). This little experiment and lengthy discussion is about what is the best way to help new users who want to dual boot Vista and Linux. I think we all kept an open mind and gave various ideas a chance to see how they play out. personally I think everyone involved did a nice service to the community. Thanks Herman especially.

---

### Post by Herman on 2009-08-23
We're all winners when can we learn something or if we can teach somebody something. :guitar:

---

### Post by Mark Phelps on 2009-08-23
> **Herman said:**
> Well if they don't have a Windows Vista DVD, how are they going to use Vista's partition editor to shrink their Vista partition then, I wonder?
Unless Vista has some way of shrinking its own partition while the operating system is mounted and running somehow, but that seems unlikely to me. 
That's exactly what it does -- it shrinks its own partition.  I know, I've done it myself.
> 
By the way, if anyone doesn't have a Vista or Windows 7 Installation disc ... It's free from NeoSmart.net, and it's only a small download.
Have you checked this recently?? NST (NeoSmart Technologies] removed their link to the ISOs because they got bott'd; replaced the links with Torrent links.  Not everyone is comfortable using Torrent links, especially folks running Virus-prone MS Windows machines.  If you don't believe me, check the links yourself.
> Give GParted it's due respect though too, I believe *when it's used correctly* it will be more than 99.999% perfect to do the job of shrinking Windows7 and Vista partitions without any boot loader problems and if you do have a boot loader problem.
As I already said, statistics don't matter when it's YOUR machine that won't boot anymore. 

I simply don't understand all this defensiveness of pressing folks to use a utility in which the release notes actually state that is is not guaranteed to work with Vista!! Presence cited the notes, which, by the way, I had previously cited myself several months ago!

I could see some of the rationale if folks had to buy a third-party utility (like Partition Magic) to shrink their Vista partition, but MS provides a free builtin utility to do that -- and it works.

And, while you probably won't believe this, I'm not fighting a win-or-lose battle with you, either.  I'm just trying to prevent folks from damaging their systems unless they have the necessary tools (in this case, a Vista DVD) to repair the damage.  It's not a personal vendetta aginst GParted; it's only an attempt to tell folks to be careful and use the Vista tool to avoid damaging their systems.

---

### Post by Herman on 2009-08-23
> [quote]By the way, if anyone doesn't have a Vista or Windows 7 Installation disc ... It's free from NeoSmart.net, and it's only a small download.            
Have you checked this recently?? NST (NeoSmart Technologies] removed their link to the ISOs because they got bott'd; replaced the links with Torrent links. Not everyone is comfortable using Torrent links, especially folks running Virus-prone MS Windows machines. If you don't believe me, check the links yourself.[/quote]Alright, thanks for the information, so they'll need to use a Ubuntu CD to download it and save it to a USB drive or something then maybe, or a freinds computer who has Ubuntu. :)

---

### Post by Herman on 2009-08-24
> As I already said, statistics don't matter when it's YOUR machine that won't boot anymore.   Have you been reading the previous posts in this thread? When used properly, GParted does not make Vista unbootable, unless you follow faulty instructions or use an an old version of GParted which was designed before Windows Vista's partitioning details became well known.
> I simply don't understand all this defensiveness of pressing folks to use a utility in which the release notes actually state that is is not guaranteed to work with Vista!! Presence cited the notes, which, by the way, I had previously cited myself several months ago!
I don't want to have to keep repeating that GParted Live CD is another distro, separate from Ubuntu. This is Ubuntu Web Forums, GParted Live CD is another distro and has its own web forum and I'm not 'pressing people' to use it. The Ubuntu installer doesn't move the start point of the Windows partition, so it is not subject to the problem, which is easily fixed anyway, if they have their repair CD, which they can download for free.
> I could see some of the rationale if folks had to buy a third-party utility (like Partition Magic) to shrink their Vista partition, but MS provides a free builtin utility to do that -- and it works.Okay, I agree with you there. I have conceded that the Windows utility seems okay, time will tell. The earlier one in Windows XP had a bad track record for corrupting a lot of partition tables, but hopefully it has been improved in Vista.
A lot of Windows users still had all kinds of trouble even with that one though, did you read the comments under the How-To Geek's '[Resize a Partition for Free in Windows Vista]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")'? 
> And, while you probably won't believe this, I'm not fighting a win-or-lose battle with you, either. I'm just trying to prevent folks from damaging their systems unless they have the necessary tools (in this case, a Vista DVD) to repair the damage. It's not a personal vendetta aginst GParted; it's only an attempt to tell folks to be careful and use the Vista tool to avoid damaging their systems.You're taking advantage of my good natured sense of humour and emphasizing something I said for fun.

I think the reason why I support Ubuntu and Open Source software should be fairly obvious. As you well know or should know by now, I have a website about how to install Ubuntu with Windows, dual booting with GRUB or other boot loaders or managers. I enjoy using Ubuntu and I want to help others to have the same opportunity.
I'm on the same side as you when it comes to trying to prevent any risk to their existing operating systems. That's why I took the time to do a lot of testing and learning on this subject many months back and it's all fully explained in my website. I don't mind if you want to advise people to use Vista's partitioner, and I have even updated my website to let Vista or 7 users know they can do so if they prefer. They'll still need to use the Ubuntu partitioner to install Ubuntu.  The thing I object to is your mistaken insistence that GParted will harm their Windows system or the bootability of it. It's simply not true, especailly not the Ubuntu installer's implementation of GParted, and implying it does is an insult to Ubuntu. If you think installing Ubuntu in the regular way will damage some other installatiion in your computer and you don't know how to fix it then you really shouldn't be taking the risk of dual booting. Just delete Windows and install Ubuntu, or keep away from Ubuntu and stick with Windows.

---

### Post by stlsaint on 2009-08-24
WOW...its nice to finally know who the guy is that im advertising for. I just made a few links in my signature to your pages herman...thanks for all you do!! presence1960 is like a legend here...if i see a thread with his name as being posted in it i pretty much consider it solved and just look to see what i can learn from him!!! thanks again!! 
(please dont consider this a thread jack!)

---

### Post by sg_57 on 2009-08-24
Hey guys, 

Having a real puzzling situation here. Little AMD64 netbook, had Vista pre-installed on it and I have already installed Ubuntu on that disk, dual-boot between Vista and Ubuntu is no problem. (by using the Vista partition re-size method from within Windows, booting from a Gparted disc was an unmitigated disaster)

I then decided to remove this hard disk, and install a fresh (faster and larger) one and try Windows 7, so installed that first. Then on to 9.04 64-bit this time.

Now, no matter what I try I am unable to get the Ubuntu 9.04 partition tool to see my Windows 7 partition at all. It keeps listing the hard disk as 'blank' without any partitions whatsoever on it, full empty space. 

Also tried 8.10 install disk. 32bit, 64bit. None work. They all list the hard disk as not having any partitions when it clearly does. Any ideas?

sg

---

### Post by presence1960 on 2009-08-24
Thanks for the generous compliment. But I want to say I am just like everyone else here. Herman does have a great page on dual booting windows & Ubuntu. herman is definitely an asset in here. There are a lot of knowledgable people in this particular community. Sometimes we may not agree, but I always believe a civilized discussion on points of contention is healthy not only for those having the discussion but also for those just reading the thread.

I tried resizing my Windows 7 partition with Gparted live using the method Herman put out there and it didn't work. But I am one of those who has to do and see so I just created another primary partition and installed Vista Home Premium OEM to it (it has been gathering dust for over a year now). As soon as my daughter is asleep tonight I am going to try resizing it as Herman suggests with the Ubuntu Live CD.

Another thing I love about Linux is that for any particular task you want to do there is usually at least two (sometimes more) different methods to accomplish the same task.

So in the end we all win because Herman has a way that works (even though I will do it tonight I believe Herman) and so does using Vista's disk management utility.

---

### Post by Mark Phelps on 2009-08-24
I must have written this a dozen times, trying each time to find a way to say this politely ... but I simply can't.

ALL I have EVER done is report what OTHERS have encountered.  I've never said that GParted is guaranteed to corrupt Vista; I've only said that it runs a risk -- which is supported in the very developer notes put out by GParted!  

I guess all of those folks who have come here devastated that their Vista systems won't boot anymore must have been lying because, after all, "it's simply not possible"!

I'm the guy that yells at speeders to slow down in rush hour traffic; I'm the guy that tells my passengers to fasten their seat belts.  And in that capacity, I've cautioned people about using GParted on Vista unless they have a Vista DVD lying around in case they have problems.

OK, so maybe I'm overcautious.  But, I'm NOT "insulting".

So, the next time some poor slob trashes their Vista system by trying the simple act of installing Ubuntu side-by-side, you GParted fans can tell them how "it's simply not possible".

I'm not going to bother anymore.

---

### Post by presence1960 on 2009-08-24
> **Mark Phelps said:**
> I must have written this a dozen times, trying each time to find a way to say this politely ... but I simply can't.

ALL I have EVER done is report what OTHERS have encountered.  I've never said that GParted is guaranteed to corrupt Vista; I've only said that it runs a risk -- which is supported in the very developer notes put out by GParted!  

I guess all of those folks who have come here devastated that their Vista systems won't boot anymore must have been lying because, after all, "it's simply not possible"!

I'm the guy that yells at speeders to slow down in rush hour traffic; I'm the guy that tells my passengers to fasten their seat belts.  And in that capacity, I've cautioned people about using GParted on Vista unless they have a Vista DVD lying around in case they have problems.

OK, so maybe I'm overcautious.  But, I'm NOT "insulting".

So, the next time some poor slob trashes their Vista system by trying the simple act of installing Ubuntu side-by-side, you GParted fans can tell them how "it's simply not possible".

I'm not going to bother anymore.
I agree mark. I have decided to add a partition & install Vista to it. I had planned on trying to resize that partition with the ubuntu installer tonight, but other things arose. Even if i am successful that in itself does not make it a "sure thing" for everyone else who tries it. I just have to see if I can get it done that way and still succesfully boot my Vista.

Even if I am successful, I will still err on the side of caution and suggest newer Ubuntu users to use the Vista disk management utility to shrink Vista. it comes down to what is best for them. If they are new to Ubuntu the odds are very high that they lack the knowledge or ability to recover their machine from that type of disaster. yes it would be a disaster to them,even though you & I may be able to smile and repair it in a matter of minutes.

Mark, please keep doing what you have been doing. You are a useful member of this community. Don't get sidetracked by discussions of doing things a different way. I favor dicussions of points of contention as long as they are cordial. In the last analysis most of us will do what is best for the people we try to help. That is why I will still suggest using Vista's disk management utility to shrink Vista. On the other hand I am curious and would like to find a way to use Gparted to do the job, but I won't be suggesting it until all the kinks are worked out and it is a well documented fact that it works well.

---

### Post by Mark Phelps on 2009-08-25
Presence: thanks for your support, really!

---

### Post by losfalme on 2009-11-04
Are there any tutorials that show you how to set up a dual boot after you have already wiped Windows off your computer and put on Ubuntu?  I was reading about gparted and how to re-partition drives with it, but it seems like all the tutorials I have found assume you have Windows on your computer to start with.  
Also, my CD/DVD drive is non functional, so I was planning to use gparted off of a USB stick, and then install Windows 7 off of another USB stick.  I was able to install Windows 7 onto a netbook off of a USB stick, but I was upgrading from Windows XP.  I found a tutorial on how to do that at Microsoft's website, using PowerISO to unpack  the .iso file.  What do I use in Ubuntu that would do the same thing?  
I have Karmic Koala installed at the moment.  Thanks in advance!

---

### Post by losfalme on 2009-11-04
OK, never mind that last question, there's a PowerISO for Linux.  NOOB FAIL!!!

---

### Post by eager2know on 2009-11-05
Has anyone tried to run an upgrade from Vista to Windows 7 on a machine that already has dual boot set up with GRUB for Vista & Ubuntu. I wonder what will happen if I start upgrading. Will the upgrade mess up my bootloader config somehow? Anyone?

---

### Post by theregdunlop on 2009-11-05
I had every problem stated with Windows 7rc installed first then trying to install 9.10.

Here's what finally worked.

Use the Windows 7 disk management utility to shrink your partition or to just leave a portion unallocated (Empty) leave it unallocated.

When installing (works with 64bit and 32 bit) and it get's to the partition portion of the installation **pick the middle option**-*not side by side or manual*. **Let it install in the largest unallocated space (that you just made). Let it install**. It won't recognize the boot. Let go into windows.

Here's where some non-newbie's may disagree with me. But I used the easy BCD 2.0 beta boot manager *you will have to register* (the 1.76 version doesn't work).

Go into add remove entires and install Linux BCD not neogrub and configure.

Reboot and Bob's your uncle. It may not be the best way but it is the only way I got it to work. 

This is my first time with Linux and with all the hype I thought the simple installation of the OS would be a little easier than it was. This may be great to the converted but what a barrier for the casual user who is curious to try it out.  

Good Luck

---

