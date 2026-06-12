---
title: "2 Seagate 750 GB HDD but only one is recognized?"
date: 2009-10-07
forum: Hardware
---

### Post by mannyfresh8 on 2009-10-07
In BIOS the 2 HDD are being recognized. However if I go into the System Monitor of Ubuntu it says something around 695 GB which i assume has to do with my partition but I am completely a noob with LINUX OS so I am trying to tackle each problem one at a time. How do I get the OS to recognize both HD? Let me know what other info you may need.

---

### Post by oldfred on 2009-10-07
I have 3 drives but in system monitor on see mounted partitions. I only have some of each drive currently mounted in this version.

try these in a terminal and see what you get

```
sudo fdisk -l

```
and 

```
sudo blkid -L
```

Some older ubuntus only sudo blkid will work. These command

---

### Post by mannyfresh8 on 2009-10-07
> **oldfred said:**
> I have 3 drives but in system monitor on see mounted partitions. I only have some of each drive currently mounted in this version.

try these in a terminal and see what you get

```
sudo fdisk -l

```and 

```
sudo blkid -L
```Some older ubuntus only sudo blkid will work. These command


Ok. The terminal indicates I have 2 drives. Disk /dev/sda: 750.1 GB and then some technical info follows about that Disk. Then it says Disk /dev/sdb 750.1 GB and then afain info about the disk but there is one big difference. 

It says:
Disk /dev/sdb doesn't contain a valid partition table


Please understand that I am a noob. I came from windows so I am new to all this. So i probably made some stupid mistake.

What do I do from here?

Oh these are SATA drives...

---

### Post by oldfred on 2009-10-07
If it is a brand new drive with nothing installed it has not been partitioned nor formatted. Suggest using gparted to look at it. You cannot use gparted on mounted drives but since it is a second unformated drive you should be able to run it from your Ubuntu install. Your install usually does not have gparted since you cannot use it on the mounted drive. 

Use synaptic to download gparted and run gparted. Do you know how you want to partition it?

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mannyfresh8 on 2009-10-07
oldfred,

I installed gparted and partitioned the drive and have the 2nd drive as the Slave and the 1st drive (Ubuntu Installed) as the Master.

As for partitioning the 2nd drive I didn't know what to do so I just used the entire drive and set it to Primary. Now the drive comes up under Places as 750.2 GB Media and if i click it. It asks to be mounted which i have no clue what thats about. Is that something I want to do?

Anyway i finally decided that I am going to need a dual boot because i use a lot of software that requires windows. So how should I go about the dual boot. I have seen several different options out there. Should I just install windows on the slave drive and leave Ubuntu where it is?

And for me to do this should I disconnect the ubuntu drive and then boot the system up to install windows xp? this way the windows install wont touch the ubuntu drive?

Whats your recommendation here? 

Sorry for all the hassle I really just want to get this system up and running the right way so I can utilize all my software.

---

### Post by oldfred on 2009-10-07
I like the idea of each hard drive being bootable which requires its own operating system and MBR linked to that operating system. That way if a drive fails you can switch drives and still boot without pulling out the liveCD. Most installs have windows on the drive and windows really likes to be first and Grub overwrites the windows MBR and automatically sets up a link to windows. Any other way is a bit more complicated but very doable. 

Disconnect Ubuntu drive and install windows in the currently new drive. You may want to think about partitioning the drive. Windows will default to the entire drive. If you partition it first you can make a smaller NTFS partition and windows will only see that to install into. I still dual boot but 3 years ago was mostly Windows now almost all Ubuntu, but I created a FAT32 shared partition for data that I wanted to see in both. I now plan to convert that shared to NTFS as FAT has many issues - no files over 4GB and other issues. 

When you plug the Ubuntu drive back in, make it primary and  you will have to manually add a boot stanza for windows so grub's menu.lst has an entry for windows.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by mannyfresh8 on 2009-10-08
> **oldfred said:**
> I like the idea of each hard drive being bootable which requires its own operating system and MBR linked to that operating system. That way if a drive fails you can switch drives and still boot without pulling out the liveCD. Most installs have windows on the drive and windows really likes to be first and Grub overwrites the windows MBR and automatically sets up a link to windows. Any other way is a bit more complicated but very doable. 
 
Disconnect Ubuntu drive and install windows in the currently new drive. You may want to think about partitioning the drive. Windows will default to the entire drive. If you partition it first you can make a smaller NTFS partition and windows will only see that to install into. I still dual boot but 3 years ago was mostly Windows now almost all Ubuntu, but I created a FAT32 shared partition for data that I wanted to see in both. I now plan to convert that shared to NTFS as FAT has many issues - no files over 4GB and other issues. 
 
When you plug the Ubuntu drive back in, make it primary and you will have to manually add a boot stanza for windows so grub's menu.lst has an entry for windows.
 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

 
 
Oh ok great this is what I was looking to do. So I just want to clear some things up first. If I use Gpartitioner and format the 2nd drive with a small NTFS partition (what would be a decent size?) I also want to be able to access the space between both OS's. What format should I make the 2nd partition on the 2nd drive?
 
Thanks again for all your help.
 
P.S. How do I modify GRUB to let me choose which drive to boot?

---

### Post by oldfred on 2009-10-08
I am not sure the size windows still needs to be, it also will depend upon which windows. You could start with 30GB to 50GB and if not enough room left for expansion expand the partition with gparted. My old WinXP with lots of stuff over 5 years is 30GB, but I have moved most data to a shared partition. You then can partition the rest of the drive as you please. NTFS for anything you may share and ext3 or ext4 for Ubuntu stuff. You could leave some unused until you know and then either expand or add another partition.

When you plug your Ubuntu drive back in as master it should boot normally. You will need a map type entry to make windows think it is on the first drive. If not in second drive first partition sdb1 or grub (hd1,0) you will have to adjust entry:

Add before or after the automagic area in  /boot/grub/menu.lst
to backup and then to edit:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```
title        Microsoft Windows  on sdb1
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by BudE on 2009-10-08
> **oldfred said:**
> I have 3 drives but in system monitor on see mounted partitions. I only have some of each drive currently mounted in this version.

try these in a terminal and see what you get

```
sudo fdisk -l

```
and 

```
sudo blkid -L
```

Some older ubuntus only sudo blkid will work. These command


Hi Oldfred,
I have Ubuntu 8.04 Hardy and wanted to know just how do you find the (Terminal) ? And though I have seen that term  SUDO...just what does it mean? I am a real noob also and trying to learn bits and pieces as I go along. 

thanks,
Bud  :)

---

### Post by oldfred on 2009-10-08
Hi BudE

Normally you should start a new thread as each thread should be on the same topic. All questions are valid especially in the       		 			[[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/#top")[**Absolute Beginner Talk   **]("http://ubuntuforums.org/forumdisplay.php?f=326")as we recognize users are new to Ubuntu & linux.

At the top of the beginner area are Sticky Threads to standard help. One of these is a free beginners guide that will help you understand Ubuntu.

Terminal is a command line rather than menu based way to issue commands to the system, for me it was like DOS which was before Apple and Microsoft had windowing systems. Terminal is in Appications on the top menu, accessories, terminal.

Sudo is a temporary super user to issue system commands. You should be sure of a command before you issue it as as super user you can also harm your system. Linux assumes you know what you are doing. That said we regularly seem to break our systems and part of the fun is figuring out how to fix it. Sometimes we break it so badly, we have to reinstall and that is why we backup, so not all is lost.


[]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by mannyfresh8 on 2009-10-09
> **oldfred said:**
> I am not sure the size windows still needs to be, it also will depend upon which windows. You could start with 30GB to 50GB and if not enough room left for expansion expand the partition with gparted. My old WinXP with lots of stuff over 5 years is 30GB, but I have moved most data to a shared partition. You then can partition the rest of the drive as you please. NTFS for anything you may share and ext3 or ext4 for Ubuntu stuff. You could leave some unused until you know and then either expand or add another partition.

When you plug your Ubuntu drive back in as master it should boot normally. You will need a map type entry to make windows think it is on the first drive. If not in second drive first partition sdb1 or grub (hd1,0) you will have to adjust entry:

Add before or after the automagic area in  /boot/grub/menu.lst
to backup and then to edit:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```title        Microsoft Windows  on sdb1
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


Thanks so much. I actually had the dual boot working perfectly with 720GB as a shared NTFS partition and Windows XP assigned to the remaining 30GB. Then on the 2nd drive I just installed ubuntu on the entire disk. I didn't even have to modify GRUB. Thats when I got greedy. I was like maybe I will partition the 2nd drive the same way as the first one. So I set Ubuntu to a 30GB partition and then a 20GB swap partition and then the remaining as free space( was going to format using windows to NTFS) but when I restarted my computer I received an error from the boot loader. 

Error 13: Invalid or Unsupported executable fromat

So I got frustrated and just reinstalled Ubuntu on the 2nd drive just as I did earlier. And the Dual boot works. But I am curious why this happened. Is it because I left that unpartitioned portion unformatted? Should I have formatted it as ext3 and then just reformatted with windows to NTFS? I am just curious at this point since I was just being greedy earlier.

Thanks again for your help. I am going to mark this thread solved since I understand how the shared drives and mounting works now. But I would still like to see what you say about this new issue.

---

### Post by oldfred on 2009-10-10
Herman's site has some of the best info around but he has a lot of info so it can be overwheming for new users unless you search for a topic or are really interested in grub, booting, installing linux, etc.
This is his discussion on error 13
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

I do not see how you got that error, perhaps the old install grub got confused with the new somehow and pointed to the wrong kernel? Normally a full install will write grub and link it to the correct menu.lst. Did you perhaps click on advanced or not install grub to the MBR when you changed your partitions around and reinstalled? We learn by doing and sometimes the mistakes make for even more learning.

I hope it was a typo on 20 GB for swap, 2GB would be fine.

---

