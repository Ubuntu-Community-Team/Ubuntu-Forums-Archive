---
title: "Ubuntu 9.10 Installation Does Not Detect Hard Drives"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mxc1090 on 2009-11-02
I can install with 8.04 LTS no problem. It detects both 320GB HDDs.  When I try 9.10 (both ubuntu and kubuntu) the partioner scans for them and comes up empty.  Opensuse 11.2 RC2 worked with ext4 flawlessly.  I don't know what could possibly be the problem. I am going to try the alternate cd tonight, but is this a common problem?  I couldn't find any information on this.

BTW...I can view, mount and manipulate the drives from the Live-CD, but when I hit install and it get to the 'select drive' part...nothing shows up.

Thanks.

EDIT: Come to think of it, 9.10-RC1 worked too along with 9.04. hmmm....

EDIT: 11-4; Alternate CD did not detect HDDs
____________________________________________________________________________________________

**_READ THIS: (2-25-2010)_**

I do not take credit for this, but if you look through the rest of the thread all of the contributors are here.

Ultimate solution:

Boot up 9.10 Live CD 

Open a terminal

type: sudo apt-get remove dmraid

then type "y" then enter

now try to install!

---

### Post by mxc1090 on 2009-11-02
bump...need help

---

### Post by BBUCommander on 2009-11-03
Not sure if this will help, but I was having the same problem on my Sager laptop.  All previous Ubuntu installers (from 8.04 on) detected my hard drive and its several partitions, while the 9.10 installer did not.

After futzing about, I stumbled upon an accidental solution.  Selecting the install option from the initial CD boot menu would result in no detected hard drives.  After restarting for the bajillionth time I walked away from the laptop in frustration.  Being unattended, the option to "Try Ubuntu" was automatically selected after the timer expired, and so when I came back I was in live-boot Ubuntu.  Oddly enough, the hard drives were there!  I am perturbed by this since selecting "Install" from the CD boot menu and then cancelling the installation also takes you into a live-boot Ubuntu, giving one the false impression that going into a live-boot directly would do no good.

Hopefully that helps since it is a rather simple solution.  Would be interested if others have experienced the same and whether the Ubutnu dev team knows about this.

---

### Post by recluce on 2009-11-03
> **mxc1090 said:**
> bump...need help

How can anybody help you, since you provide no details whatsoever?

---

### Post by mxc1090 on 2009-11-03
> **recluce said:**
> How can anybody help you, since you provide no details whatsoever?

True.


BBUCommander I tried it both ways...no go, but thanks.


Details:

Mobo: gigabyte p35-ds3p
CPU: 2.66 Intel E6750 Core 2
HDD1: Seagate Barracuda 7200.10(11?)  (320gb)Sata2
HDD2: Western Digital WD3200          (320gb)Sata2
Vid: XFX Nvidia 8600gt
Memory: Geil 2x1gb 800mhz

(Note: Hard drives were both in a raid 0 (striping) setup before I removed windows. Since then I deactivated raid on the Mobo and formatted HDDs.  I have tried 'dban' to erase the hdds, but that seems to fail wiping them.)

---

### Post by Ownager on 2009-11-03
> **mxc1090 said:**
> I can install with 8.04 LTS no problem. It detects both 320GB HDDs.  When I try 9.10 (both ubuntu and kubuntu) the partioner scans for them and comes up empty.  Opensuse 11.2 RC2 worked with ext4 flawlessly.  I don't know what could possibly be the problem. I am going to try the alternate cd tonight, but is this a common problem?  I couldn't find any information on this.

BTW...I can view, mount and manipulate the drives from the Live-CD, but when I hit install and it get to the 'select drive' part...nothing shows up.

Thanks.

EDIT: Come to think of it, 9.10-RC1 worked too along with 9.04. hmmm....

Hi, I am familiar with your issue. You will need to burn ubuntu 9.10 iso into a cd first before you read my quote in my thread. I am sure that it will help you to solve this problem. I found a trick. It's helpful. 

[http://ubuntuforums.org/showthread.php?t=1283579](http://ubuntuforums.org/showthread.php?t=1283579)

Read my quote from my last post. 

Cheers!

---

### Post by mxc1090 on 2009-11-04
Thanks Ownager, but as I stated: "I can view, mount and manipulate the drives from the Live-CD."

I have done what you said to do in your other post, but that only shows me my HDDs, when I go to install *thats *where they are not detected.

---

### Post by Ownager on 2009-11-04
Hi, do you have Ubuntu 9.04 version too? When you say yes, you can test 9.04 version in install. It should recognize your hard drive for you. 

Does bios settings recognize your hard drive? And how did you update from 9.04 version to 9.10 version?

---

### Post by mxc1090 on 2009-11-04
> **Ownager said:**
> Hi, do you have Ubuntu 9.04 version too? When you say yes, you can test 9.04 version in install. It should recognize your hard drive for you. 

Does bios settings recognize your hard drive? And how did you update from 9.04 version to 9.10 version?

Yes. As I stated: "Come to think of it, 9.10-RC1 worked too along with 9.04."...by *worked *I mean that it would install flawlessly.

And yes the BIOS detects them at POST.

---

### Post by Ownager on 2009-11-04
Ok, you should do the same as what jpeddicord said about upgrading from 9.04 to 9.10 version. 

You may read it. You probably did. I am trying to do my best to help you. 

Is your 9.04 version installed? 

Please read this thread. 

[http://ubuntuforums.org/showthread.php?t=1305158](http://ubuntuforums.org/showthread.php?t=1305158)

---

### Post by mxc1090 on 2009-11-04
Thanks Ownager for your continued help.

As of now I have settled for 8.04 LTS x32 mostly because everything "just works".

It is possible for me to upgrade from 9.04 to 9.10, but then I miss out on ext4 and GRUB 2. These would be some of bigger reasons for my upgrade to 9.10. And to be honest 8.04 and 9.04 aren't *that* different. Plus, I feel a clean install of 9.10 would be less problematic than and upgraded version of 9.04 (but that's just an assumption).

---

### Post by ario on 2009-11-05
Guys I read this thread from up to down and from page 1 to this position completely. Because I have the same problem and I guess you there have not find any solution to solve this problem.
I have a 320GB SATA disk on sda and a 160GB SATA on sdb.
When booting with Install option it will not detect 160GB HDD but detects 320GB one! (But I won't install it on my 320GB HDD, So this way is useless).
When booting with try ubuntu without... option It will detect both HDDs on gparted but installer doesn't.
When booting with Install Option and clicking on <quit> button in select partition page of install wizard and then bringing the live cd environment up, Again gparted detects both HDDs but installer does not.
I guess this is a bug in installer software and us must wait for 10.04 version of ubuntu to get the latest software. This is what I call it Crap:(
I left KDE and migrated to gnome because since its 4th edition it never be the same as before and every where was lots of bugs to hang with... now I must left 9.10 and wait for next version:(
P.S. I already have Ubuntu 9.04 32bit installed without any problem.
P.S. My System Specification:
Mainboard: k9n neo v2
chipset: nvidia nForce 520
HDD1: SATA 320GB
HDD2: SATA 160GB
CPU: AMD x2 4400+
Any other suggestion?
Thanks for your attention guys.

---

### Post by mxc1090 on 2009-11-05
^^^Yep pretty much the same problem.  I understand there are a lot of problems with Karmic installs.  I am willing to sit this out for a few weeks and come back when some bugs are weeded out... unless someone has a specific solution to this now, that would be great. I feel it *must* be Karmic related, but it could also be something I did with RAID that it doesn't like. 

I guess I'll deal  :-({|=

...for now.

---

### Post by shoegoo on 2009-11-05
Add me to the list of people experiencing this problem.  Attempting install on a Gateway LX6810-01.  There is only 1 drive on what looks to be an NVidia RAID controller (RAID can't be disabled).  I will post an lspci when I get back to working on it.  The drive works and is detected in the BIOS.  I was able to use gparted to erase the Windows partitions and recreate new ones.  No luck in Ubiquity though.

EDIT:  Found this thread [http://ubuntuforums.org/showthread.php?t=1301697](http://ubuntuforums.org/showthread.php?t=1301697) which also links to the bug report for this issue.  Solution is to apt-get remove dmraid.  It worked for me.

---

### Post by mxc1090 on 2009-11-06
> **shoegoo said:**
> EDIT:  Found this thread [http://ubuntuforums.org/showthread.php?t=1301697](http://ubuntuforums.org/showthread.php?t=1301697) which also links to the bug report for this issue.  Solution is to apt-get remove dmraid.  It worked for me.

ooooo....this could help. I'm excited. I'll let you know what happens when I get home tonight.

---

### Post by mxc1090 on 2009-11-06
> **mxc1090 said:**
> ooooo....this could help. I'm excited. I'll let you know what happens when I get home tonight.

```
m***@T***:~$ sudo apt-get remove dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dmraid is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

I'm guessing this means it won't affect it. :(

---

### Post by Yoey on 2009-11-06
I had the same problem.  I could see and work with the hard drive in gparted but when the installer came to the partitioning stage, it couldn't see anything.

after running "sudo apt-get remove dmraid", the installer worked.

---

### Post by Ginsu543 on 2009-11-06
I had the same problem until I ran sudo apt-get remove dmraid. I followed these steps:

1) Boot into Ubuntu 9.10 using LiveCD (without installing)
2) Open Terminal and run sudo apt-get remove dmraid
3) Start the installer by double-clicking on its icon on the desktop

After that, the installer could see my drives and I was able to install. One more thing, if you install GParted later, it will reinstall dmraid as part of its package. I didn't know that, installed GParted, and then when I rebooted I could no longer access my second SATA drive. When I manually removed dmraid again, everything was normal.

---

### Post by jurisz on 2009-11-07
I still have empty screen on partitions page. 
In Gparted and Disk Utility  see hdd, i have it also listed under My Places
and can mount unmount it,  but when i start install the partition screen is simply empty.

---

### Post by Templar Boe on 2009-11-07
I just installed 9.10 and according to Ginsu543's observations, opened the terminal from the live C.D. and removed dmraid with the following command line:
 
sudu apt-get remove dmraid
 
I confirmed that I wanted to do that and the process began and completed successfully.
 
My hard disk drive then became visible in the disk partition application and I was able to install 9.10
 
The full process is as follows:
 
Boot live C.D.
 
Open Terminal which is available at one of the drop down menus at the top right of the desk-top; sorry I'm not sure which I'm just beggining to use to Linux O.S.
 
Type:
 
sudo apt-get <--them press enter-->
 
Type 
 
sudo apt-get remove dmraid <--then press enter-->
 
Confirm your request by selecting (y/n) y key <--then press enter-->
 
Click the hard-drive image on the live C.D. desktop to begin the installation.
 
Your hard drive will be visible on the disk partition utility now.

---

### Post by freackout on 2009-11-07
> **mxc1090 said:**
> True.


BBUCommander I tried it both ways...no go, but thanks.


Details:

Mobo: gigabyte p35-ds3p
CPU: 2.66 Intel E6750 Core 2
HDD1: Seagate Barracuda 7200.10(11?)  (320gb)Sata2
HDD2: Western Digital WD3200          (320gb)Sata2
Vid: XFX Nvidia 8600gt
Memory: Geil 2x1gb 800mhz

(Note: Hard drives were both in a raid 0 (striping) setup before I removed windows. Since then I deactivated raid on the Mobo and formatted HDDs.  I have tried 'dban' to erase the hdds, but that seems to fail wiping them.)
ive had a bit of fun with raid drives similar to you however i found that some installers similar to ubuntu debian ect, are not all the same at automatically picking up these alterations ie when you de activate the raid using many differing methods ( ie dynamic drives lvm's partitions ect), however i found the suse install disks where most helpfull, other times i got one drive back but not the other, which seemed a little confusing. switching off the electric after the partitioning, silly but it helps. then putting my fav ubuntu back on. yep experimentation with hdd programmes sometimes works 4 you. also try pmagic 4.5 thats good.

---

### Post by Cr0n_J0b on 2009-11-07
Well, I'm through with my installation hell with Ubuntu!  I have to say that I'm really disappointed with the release.  The installation has several big issues and this is one of them.

I had the same issue and after messing around for hours and swapping drives I think I figures it out.

I agree that it has something to do with DMRAID.  I think that the partitioner looks for "free" disks that have no MBR or something like that.  I tested this out and sure enough if I added a brand new disk to the system, the partitioner would pick it up, but if i added a disk from a previous installation it would not.  I was thinking that zeroing out the MBR might be the way to fix it, but I never got that far.

---

### Post by mxc1090 on 2009-11-08
> **shoegoo said:**
> 
EDIT:  Found this thread [http://ubuntuforums.org/showthread.php?t=1301697](http://ubuntuforums.org/showthread.php?t=1301697) which also links to the bug report for this issue.  Solution is to apt-get remove dmraid.  It worked for me.

Ok...I misunderstood the first time. I did not understand that sudo apt-get remove dmraid had to be executed through the liveCD. Of course that would make sense, but I'm kinda slow. Anyway **I tried it and it worked!** That was my problem and I can now say that this is solved. Thanks everyone.:D

---

### Post by DenKriger on 2009-11-08
> **Ginsu543 said:**
> I had the same problem until I ran sudo apt-get remove dmraid. I followed these steps:

1) Boot into Ubuntu 9.10 using LiveCD (without installing)
2) Open Terminal and run sudo apt-get remove dmraid
3) Start the installer by double-clicking on its icon on the desktop

After that, the installer could see my drives and I was able to install. One more thing, if you install GParted later, it will reinstall dmraid as part of its package. I didn't know that, installed GParted, and then when I rebooted I could no longer access my second SATA drive. When I manually removed dmraid again, everything was normal.

This worked for me! thanks! :D

---

### Post by ntiy on 2009-11-09
works here as well. thanks for posting solution.

---

### Post by rampage_1973 on 2009-11-20
if you are like me and upgraded 1 computer and everything was fine( cause it did not have a second sata drive) then upgraded your desktop (which did have more than 1 sata drive) then you might be interested to know that removing dmraid after you have installed also worked, to be clear i did sudo apt-get remove dmraid , when it finished i rebooted and then i was able to mount my 2nd and 3rd hard drive!!
so thanks to all of you that found the solution before me! i still think ubuntu rocks and i am now not even using windows (skipped the vista upgrade) (and i am a pc and i use ubuntu 9.10 because it is my choice it is fun and windows 7 and the miserable empire known as microsoft can keep their crap!) 
and they really should start paying the for the items they "borrow" from linux/unix
and quit trying to patent software that has been around longer than they have.

k i am done ranting now, thanks to you all and the open source community you are the true innovators & dreamers in the world.

---

### Post by Mi11z on 2009-11-20
> **recluce said:**
> How can anybody help you, since you provide no details whatsoever?


lol is all i can help you out with regarding this subject. ;)

---

### Post by ario on 2009-11-22
rampage
we are glad that you are so happy with you installation:)

---

### Post by brc816 on 2009-11-22
I followed Ginsu543's recommendations to the letter, and they worked for me, too. Previously, I had a VERY bitter experience wherein I somehow managed to lose the partition table of my 250GB USB drive, which was very painful since I use it to boot various Linux distros that I install for testing, etc.

My customary practice is to install a test system onto a single partition on the drive, which is usually about 50GB. I have a GRUB (not GRUB2) installed on that spindle's MBR and from there, the grub.conf/menu.lst dispatches to the GRUB installed on the distro-specific partition. Whether this is the Best Practice or not is irrelevant - it works for me, I understand it, and can deal with strange problems as needed.

So, in this case, I booted one of the other distros, used it to (re-)format the partition I'd designated for Ubuntu, using ext3, and then shut it down, and rebooted the system with the Ubuntu installation CD. Everything went well - I made sure to, despite the vociferous objections from the installer, have GRUB2 installed on Ubuntu's partition (/dev/sdc7) only. After the installation CD completed its work and signified that it was time to reboot, I did so, and everything came up perfectly!

---

### Post by HeadHunter00 on 2009-11-22
It doesn't if the cd is broken.

---

### Post by sideaway on 2009-11-29
sudo apt-get remove dmraid worked for me too! thanks. But now I can't get Grub2 to boot my new install.

This is by far the worst Ubuntu install experience I've had since 7.04 :(

---

### Post by mightyiam on 2009-12-20
This is how I solved it:
[https://bugs.launchpad.net/ubuntu/+source/partitioner/+bug/461470/comments/14](https://bugs.launchpad.net/ubuntu/+source/partitioner/+bug/461470/comments/14)

---

### Post by zappadragon on 2010-02-19
> **Ginsu543 said:**
> I had the same problem until I ran sudo apt-get remove dmraid. I followed these steps:

1) Boot into Ubuntu 9.10 using LiveCD (without installing)
2) Open Terminal and run sudo apt-get remove dmraid
3) Start the installer by double-clicking on its icon on the desktop

After that, the installer could see my drives and I was able to install. One more thing, if you install GParted later, it will reinstall dmraid as part of its package. I didn't know that, installed GParted, and then when I rebooted I could no longer access my second SATA drive. When I manually removed dmraid again, everything was normal.

OK so this did not work for me!!! It said it was a read only version and it could not remove. I can see the drives in Gparted but I can't do anything to them and an fdsik -l does not show anything. Any ideas

---

### Post by winter123 on 2010-02-23
> **Ginsu543 said:**
> I had the same problem until I ran sudo apt-get remove dmraid. I followed these steps:

1) Boot into Ubuntu 9.10 using LiveCD (without installing)
2) Open Terminal and run sudo apt-get remove dmraid
3) Start the installer by double-clicking on its icon on the desktop

After that, the installer could see my drives and I was able to install. One more thing, if you install GParted later, it will reinstall dmraid as part of its package. I didn't know that, installed GParted, and then when I rebooted I could no longer access my second SATA drive. When I manually removed dmraid again, everything was normal.

Did this exactly, got some file not found errors but the command finished. But installer still can't find my hard drive. Everyone is like wow, just typed the one line and it magically worked. Well not for me. Any other ideas?

EDIT: After all the problems i had installing kubuntu 9.10 i finally got it!!! Since this is such a huge thread, I'll write some stuff here. If someone is having this problem and the sudo command doesn't work... download the alternate (text-based) cd. It recognized my disk for whatever reason. And, continuing on... Make sure to first use the "check disk" option so burn errors are out of the equation. Then, when asked how to partition, choose manual, it's a lot easier to tell what's going on and what you're doing. go to your windows partition(or if you don't have one skip this) and hit enter, then resize. Type a size around 95% probably. Then select the free space that was created and click automatically allocate. Then go to done, and the installation takes 45 minutes or so, and that should be it.

---

### Post by ChrisThompson on 2010-02-25
I am also having this problem and, unfortunately, nothing seems to be helping.  I'm trying to set up ubuntu on my desktop.  It used to run very well on an old PATA drive, but that drive has recently decided after 7 years of service to pursue a career as a doorstop.  While it ran, ubuntu never noticed my two SATA drives that house my XP build and storage system.  I initially tried to get them to detect but it proved to difficult and I eventually gave up.  Now, without the PATA drive, I have no choice.

I'm trying to dual-boot onto the drive that houses XP, a Maxtor 6e040t0, 40 gig SATA drive.  When I get to the partitioning stage of setup my drive never shows up to the partitioner.  I have tried the following:

-booting with the live CD and removing dmraid, both from terminal and Synaptic.  Even after dmraid was removed the drive was not detected and did not show up on GParted.
-installing off of the text-based cd. Again, I would get all the way to the partitioning phase, but the drive never showed up on the partitioner.  EDIT:  To clarify, it does not detect anything in the "detect disks" phase, and offers me a list of drivers to download.  Since I don't see a driver for my disk I select "continue with no disk drive."  When it gets to "partition disks" it can only undo changes it never made or write changes to a disk it doesn't know is there.
-disconnecting my second drive and trying again.  This made absolutely no difference.  I have no RAID connection of any kind between the two drives, they run completely independently of one another, but someone recommended it on another page and I gave it a shot.
-installing other ubuntu builds.  I have tried this with 8.10 and 10.04 alpha with identical results.  (Side note, the 10.04 alpha problem really troubles me, as it leads one to believe that this problem will not be addressed in 10.04's final release).
-changing the drive's definition in BIOS.  My Mobo (ASUS A8V-XE with Phoenix - AwardBIOS) has three options for SATA controllers: IDE, RAID, and AHCI.  When I built the computer it defaulted to IDE, and I never needed to change it until this happened.  I've tried all three options, and changing either of these options caused the Windows build to stop working.  Admittedly, this is the option I've explored the least, since changing things in BIOS always makes me nervous, and I don't want to start poking around in there unless I have a definite game plan.  EDIT:  I have gone through all three configurations and turned the SATA controller off and both the LiveCD and the alternate-text, with no change.

So that is the situation.  My xubuntu setup on my laptop is still chugging along, but I'd hate to be relegated to XP on my desktop just because my PATA drive died.  Any insight anyone can provide into this situation is greatly, greatly appreciated.  Thanks.

---

### Post by ChrisThompson on 2010-03-06
Solved the problem!  I needed to boot pci=nomsi and then it detected the disks.  [Here's my detailed post on how to do this.]("http://ubuntuforums.org/showthread.php?t=1421942")

---

### Post by clarktrip1 on 2010-09-10
I know I'm late to the game on this, but thanks, Chris Thompson.  I have the exact same motherboard and was trying to install on a new, never used, fully zeroed out Seagate 250G SATA 2 drive ST3250318AS.  I was losing hope until I read your posts 35 & 36.  I set pci=nomsi as you did and can see the disks.  I'm installing Ubuntu Studio 10.04 (alternate DVD so I can use LVM). 

Thanks!

---

### Post by mnemonic76 on 2011-07-17
Fantastic! This solution worked for me. Compaq Presario 5000. (5012US) Ubuntu installers newer than 9.04 would not see the disk, although from a shell fdisk -l /dev/sda would see the disk fine.

Also had this problem with Peppermint OS installers too.

Thanks!

---

### Post by rad0n on 2011-10-13
I had the same problem with ubuntu 11.10 today
but i couldn't remove dmraid package. the prompt told me that it could not get access to the package db as if another process was using it ... obviously the installer itself

-------------------------------------------------------------------------------------------------
Following steps worked for me:
1) list kernel modules for raid support
lsmod | grep raid 
dm_raid45
...
2) and remove them
modprobe -r dm_raid45

3) go back to the installer screen.
4) back and next on the installer screen
and it rescanned my partitions and found my hard drive
-------------------------------------------------------------------------------------------------

My bios setting for the sata controller was ide (ahci was same problem) - there was a raid option, too - might be another way to fix it by switching sata controller mode to raid. 
Didn't test this strategy tough.

/var/log/syslog had no particular error messages
There was a message that it did detect a sata raid controller and if i don't like it i should boot with the option 'nodmraid'. This might work, too.

My SATA Controller:
Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)

---

