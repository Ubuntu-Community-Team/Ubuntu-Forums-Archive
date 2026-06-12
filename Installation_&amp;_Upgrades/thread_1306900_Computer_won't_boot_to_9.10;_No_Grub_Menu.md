---
title: "Computer won't boot to 9.10; No Grub Menu"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by S0C0M988 on 2009-10-30
My computer is running Windows 7 Pro 64-bit, and I shrunk the partition to accommodate Karmic Koala.  I installed it, and everything went just fine, but when I rebooted it went straight to windows.  I tried doing a fresh install with just Ubunutu and again, everything installed just fine but it wouldn't boot.  The error message stated something along the lines of "Insert boot device and press Enter to continue."  Any help here would be great b/c I'm an avid Ubuntu user.  I always keep a Windows dual boot around just in case, but have no intention of switching back. 

Thanks!

---

### Post by Herman on 2009-10-30
It could be that GRUB wasn't installed in the correct hard disk or you might have a CMOS setting (BIOS) which prevents any programs writing to your first hard disk's MBR.

You should be able to try again to install GRUB 2 to MBR using your Ubuntu Karmic Koala 'Desktop' Live/Install CD.

Try booting with your Live CD and then mount your hard disk installed Ubuntu operating system. 
Take a look in /media to see what the name of the mount point is or ls /media,
```
ls /media
```You should get a nice user-friendly name for the mount point if you set a file system label, otherwise you might get a file system UUID number which can be rather long and cumbersome. 
You can set a file system label by right-clicking on your partition in GParted, for example I simply call mine KARMIC.

Regardless of whether you set a label for your file system or you're happy to stick with the UUID number, open a terminal and run the following command,
```
sudo grub-setup -d /media/KARMIC/boot/grub /dev/sda
```Where /media/KARMIC is the mount point for your Ubuntu file system, otherwise it could be some other name or a UUID number. Feel free to replace as appropriate.

If it complains about not being able to open /boot/grub/device.map, you might need to hold it's hand and specify the path to the device.map file with the -m option, as follows,
```
sudo grub-setup -d /media/KARMIC/boot/grub -m /media/KARMIC/boot/grub/device.map /dev/sda
```If it still doesn't work try looking in your CMOS and disabling any MBR write-protect feature you may have left enabled, it may also be called something like 'boot sector antivirus' or some other name.
If your computer has more than one disk you might need to change the '/dev/sda' part of the command to /dev/sdb or something else.

---

### Post by flower71 on 2009-10-30
Absolutely wonderful, Herman!!  Your instructions were clear, and concise, and worked beautifully!  I had myself all set to spend the next 2 or 3 hours researching grub2 and trying to figure out what I had to do to fix this issue... but with your post, it took me about 4 minutes (and 3 of it was finding your post!)

This should really be stickied at the top, there are a lot of other folks out there running into this problem trying to install Karmic, and most of them seem to resort to reinstalling grub to get it working...

PS  I should clarify - I actually used this to fix the grub error 15 I got after installing; I have 4 ubuntu installs over 2 different hard drives and something about my setup seemed to confuse grub2.  My problem didn't have anything to do with having a separate Windows install as in the parent post, since I don't even have Windows...

---

### Post by Herman on 2009-10-30
:D  Thanks for the nice feedback, I'm happy for you that yours was able to be fixed using the easiest and simplest possible solution. 
Happy Ubuntuing :D

---

### Post by axel_2078 on 2009-10-30
I wish I could say this also worked for me. I keep getting "grub-setup: error: Cannot open `/media/Karmic/boot/grub/device.map'"

This is driving me nuts. I can boot just fine from the Live CD, but not after the installation.

---

### Post by Herman on 2009-10-30
> I wish I could say this also worked for me. I keep getting "grub-setup: error: Cannot open `/media/Karmic/boot/grub/device.map'"
:D If it complains about not being able to open /boot/grub/device.map, you might need to hold it's hand and specify the path to the device.map file with the -m option, as follows,
```
sudo grub-setup -d /media/KARMIC/boot/grub **-m /media/KARMIC/boot/grub/device.map** /dev/sda
```

---

### Post by axel_2078 on 2009-10-30
I guess I mistyped it the first time because I ran it again and this is what I got:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: If you really want blocklists, use --force.

---

### Post by Herman on 2009-10-30
Oh, you are probably installing GRUB to a partition boot sector then I guess, instead of to a MBR.
That's okay, just use the -f option then, for --force. GRUB 2 doesn't like being installed to a mere partition boot sector, so it will grumble and complain but it will do it. 

Try this then,
```
sudo grub-setup **-f**  -d /media/KARMIC/boot/grub -m /media/KARMIC/boot/grub/device.map /dev/sda
```

---

### Post by electrofunky on 2009-10-31
Thank you, thank you, thank you! You saved me the great hassle of spending potentially hours trying to figure out what was wrong with my 9.10 installation.

Cheers!
:D

-Dean

---

### Post by flower71 on 2009-11-05
Just had to write in and thank you again - installed Karmic on another pc and again had problems with Error 15 and grub2.  That's three pc
s now - the one I installed on sda had no problems, but the ones I installed on sdb and sdc needed me to step in and run update-grub from the livecd.

Sooooo happy for this post!

---

### Post by gackt on 2009-11-14
AH Live saver live saver live saver

one thing doug, if you keep getting Cannot open `/media/Karmic/boot/grub/device.map' then i suggest you mount the file system first. I was stupid enough and stressed enough not to mount the file system ( just click the drive on the explorer)...of course it cann't look for the file what am i thinking!!. 

Thanks!

---

### Post by darkod on 2009-11-14
@Herman
This short and precise procedure how to reinstall grub2 deserves a sticky. I've seen a number of threads here past few days asking how to reinstall grub2 but I have no experience with it to help personally.

---

### Post by Nimnio on 2009-11-17
I did a clean install of Windows 7 which (as expected) replaced Grub, and to get Grub back up and running, Herman's advice worked perfectly! After reinstalling Grub2 as instructed, I used update-grub2 (as per [this post]("http://ubuntuforums.org/showthread.php?t=1195275"), point 6) to get Grub to add Windows 7 to the list.

[SIZE="1"]Noob advice: Just getting into Windows/Linux dual-booting? Install a second hard drive. Install Windows on the first drive. In your bios, change the drive order, and then install Linux (and Grub) on the second hard drive. This way you can protect Window's sensitive MBR. As a beginner, I find this technique reassuring.[/SIZE]

---

### Post by palewire on 2009-11-30
If `ls /media` returns an empty directory, what does that mean? Did I incorrectly boot from the Live CD?

---

### Post by nimajiman on 2009-12-02
> **palewire said:**
> If `ls /media` returns an empty directory, what does that mean? Did I incorrectly boot from the Live CD?

No, I doubt you booted incorrectly from the CD, you probably just haven't yet mounted the partition you actually installed Ubuntu on.

As you are running straight from the liveCD, you need to tell the 'live' version to read from the hard drive that you installed Ubuntu on.

It should be as simple as clicking 'places' up the top left and then clicking the label (or XX GB Filesystem) etc that you installed to. Then try "ls /media" again and see what comes up.

---

### Post by MikeCheck on 2009-12-03
This worked for me also.  Thanks a lot for the instructions.

---

### Post by PaulInBHC on 2009-12-04
This saved me a lot of searching today. I resized my partitions.

Thanks for the grub2 info and the tip on labeling drives. I've wanted to be able to tell from places just what the heck I'm looking at when I've got 4 or 5 partitions.

---

### Post by adonet on 2009-12-16
I'm sorry to say that It still doesn't work for me. I'm trying to install Grub 2 in the partition of Linux Mint 8. 

This is what I get:

mint@mint ~ $ sudo grub-setup -f -d /media/Mint8/boot/grub -m /media/Mint8/boot/grub/device.map /dev/sda9
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

Do you have any suggestion?

Thanks Jeroen

---

### Post by madmaze on 2009-12-16
> **S0C0M988 said:**
> My computer is running Windows 7 Pro 64-bit, and I shrunk the partition to accommodate Karmic Koala.  I installed it, and everything went just fine, but when I rebooted it went straight to windows.  I tried doing a fresh install with just Ubunutu and again, everything installed just fine but it wouldn't boot.  The error message stated something along the lines of "Insert boot device and press Enter to continue."  Any help here would be great b/c I'm an avid Ubuntu user.  I always keep a Windows dual boot around just in case, but have no intention of switching back. 

Thanks!

sounds to me like a bad MBR =/ happend to me a few months ago.. sometimes you can fix it with M$ recovery console.. 
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by 2ways on 2009-12-16
Hi Folks,

I'm installing 9.10 on a Sony Vaio laptop (pcg-frv31) and am having trouble booting from the hard drive.

I've installed 9.10 from the CD and it's all 'there' as it were, but when I remove the CD ad reboot, I get 'operating system not found'.

The problem seems to be along the lines of what's being discussed here, so I have tried all the ideas above, but to no avail.

1. There doesn't seem to be any protection on the MBR in CMOS.

2. Originally, /media was empty when I tried listing the contents, so I clicked on the main partition in Places and that mounted it, but when I rebooted, it still can't find the operating system and when I tried 'ls /media' after rebooting, it was empty again.  That is, I had to re-mount the filesystem.

3. The option to label my mount point in GParted is greyed-out in the right-click menu, but I would love to rename it!  How can I do it?

4. There is no device.map in grub.  /media/'mountpoint'/boot/grub is empty.
 

 5. When I reboot to the live CD, all location information is gone, time is wrong, etc.  That is, nothing in my proper installation has taken hold.
 

 6. I have tried to re-install Ubuntu from the CD and, at the partitioning stage, it tells me that Ubuntu is the operating system installed on the partition I am about to reformat, so Ubuntu thinks that Ubuntu is installed.


 The upshot is that 9.10 just isn't installing properly.  The CD with the disk image checks out fine.
 

 Thanks for any help.
 

 Lewis

---

### Post by darkod on 2009-12-16
> **lewis.jones@reap.asn.au said:**
> Hi Folks,

I'm installing 9.10 on a Sony Vaio laptop (pcg-frv31) and am having trouble booting from the hard drive.

I've installed 9.10 from the CD and it's all 'there' as it were, but when I remove the CD ad reboot, I get 'operating system not found'.

The problem seems to be along the lines of what's being discussed here, so I have tried all the ideas above, but to no avail.

1. There doesn't seem to be any protection on the MBR in CMOS.

2. Originally, /media was empty when I tried listing the contents, so I clicked on the main partition in Places and that mounted it, but when I rebooted, it still can't find the operating system and when I tried 'ls /media' after rebooting, it was empty again.  That is, I had to re-mount the filesystem.

3. The option to label my mount point in GParted is greyed-out in the right-click menu, but I would love to rename it!  How can I do it?

4. There is no device.map in grub.  /media/'mountpoint'/boot/grub is empty.
 

 5. When I reboot to the live CD, all location information is gone, time is wrong, etc.  That is, nothing in my proper installation has taken hold.
 

 6. I have tried to re-install Ubuntu from the CD and, at the partitioning stage, it tells me that Ubuntu is the operating system installed on the partition I am about to reformat, so Ubuntu thinks that Ubuntu is installed.


 The upshot is that 9.10 just isn't installing properly.  The CD with the disk image checks out fine.
 

 Thanks for any help.
 

 Lewis

Boot with the cd, Try Ubuntu option, open terminal and execute:
sudo fdisk -l

Copy the result here. That's for start. :)

---

### Post by 2ways on 2009-12-16
Thanks.  Here it is.

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d70e729

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

---

### Post by darkod on 2009-12-17
> **lewis.jones@reap.asn.au said:**
> Thanks.  Here it is.

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d70e729

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

It looks like you have running ubuntu. If you want to reinstall grub2 in case it's messed up, boot with the ubuntu cd, Try Ubuntu option, and in terminal execute:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will reinstall it on the MBR of /dev/sda using the mounted /dev/sda1 as root (which is your root partition). Easier then using the /media commands and it gets the same result.
Reboot without the cd and check if anything has changed.
If still not working, report what exactly is the problem because you continued another thread and it's difficult to follow what exactly is your problem.

PS. Note that if ubuntu is the only OS on your computer you will not see grub menu at start. Ubuntu will just start. That's because there is no other OS to select anyway. It should start normally and work.

---

### Post by 2ways on 2009-12-17
Thanks, Darko.

I've tried re-installing grub.  That installed grub, but didn't solve my problem.  I've moved my problem to a new thread at [http://ubuntuforums.org/showthread.php?p=8513870#post8513870](http://ubuntuforums.org/showthread.php?p=8513870#post8513870) where you can get more detail.

One of things that's annoying in all this is that it takes 30 minutes for ubuntu to boot from the CD, so every time I try a new idea and then reboot, it means another 30 minutes of waiting!  Unless, of course, the problem is fixed, but, alas, so far I haven't achieved those dizzying heights.

I am very excited about ubuntu, however.  Can't wait to get it going!

Thanks for the help.

Lewis

---

### Post by Jefferythewind on 2010-01-20
Hey, This post really saved my night, i have been working on getting back to my ubuntu 9.10 system all day since installing XP on a dual boot.  I think I inadvertently installed grub2 when I had grub legacy leftover from my 9.04, anyway this method got me back!!! I love it.

---

### Post by rahul_bhise on 2010-02-28
i also have same problem as [adonet]("http://ubuntuforums.org/showpost.php?p=8508460&postcount=18") #18
```
ubuntu@ubuntu:~$ sudo grub-setup -f  -d /media/ro910/boot/grub -m /media/ro910/boot/grub/device.map /dev/sdb11
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
[COLOR="DarkSlateGray"]grub-setup: error: Cannot read `/grub/core.img' correctly[/COLOR]
ubuntu@ubuntu:~$
```
lets wait for harman

---

### Post by Herman on 2010-03-03
Try installing GRUB2 to the MBR of a hard disk instead of to a partition boot sector and see if that works.

---

### Post by davesbrain on 2010-03-17
Please help. This is getting frustrating.
I have one hard drive and one operating system on that one drive. No dual boot, no raid, no windows, no usb boot. Just 9.10 installed on one 40 gb drive. After trying the various techniques from this forum, I'm now stuck at Grub loading, error, grub rescue prompt. No menu list to choose from or edit (e).
Here is the output of 'sudo fdisk -l'
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4677    37567971   83  Linux
/dev/sda2            4678        4863     1494045    5  Extended
/dev/sda5            4678        4863     1494013+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Tried this (which worked in the past):
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

now it gives me this when I try that:
> cp: not writing through dangling symlink `/mnt//boot/grub/gfxterm.mod'
Never did that before.

And when I try and reboot it gets stuck at grub loading, can't find file, grub rescue.

(This started with a spontaneous reboot(don't know why), which of course didn't reboot properly and dumped me at the initramfs prompt)
davesbrain is online now Report Post   	Edit/Delete Message

---

### Post by Herman on 2010-03-18
The first thing to do would be to run a file system check.
If the file system check is able to be completed with no problems you can try to boot, but if it fails with an error message, make a note of the error.

You can run a file system check by right-clicking on your partition from GParted Partition Editor in your Ubuntu Live CD.
If you like the command line you may like to use this command,
```
sudo e2fsck -C0 -p -v -f /dev/sdx,y
```
This command will either fix your file system or at least report useful information if it encounters errors which require further investigation.
The command GParted runs is almost the same and it also reports useful info if you click for the drop-down menus in the file system check dialog box GParted.

---

### Post by davesbrain on 2010-03-18
It's now 2 AM. When I booted with live cd for internet help, I opened my home directory (not the live cd home) to be clear, and it was EMPTY! Perhaps a noob thing, but all my stuff should have been there. EMPTY! So I thought at that point I might as well just do a clean install from fresh. Install went smoothly, applied all updates. When it was finished a reboot was required...wait for it......INITRAMFS!

I'm beginning to think this is just garbage. Our IBM 8088 downstairs boots up just fine.

Any ways, I do appreciate the help. This is ridiculous.

Boot
Up
My
Box

---

### Post by Herman on 2010-03-18
It seems as if you could have a hardware problem of some kind, but I'm not sure.

I'm only guessing, but maybe there's something wrong with the hard disk.
Can you open 'System' --> 'Adminsitration' --> 'Disk Utility ' ,and use the Palimsest Disk Utility to look in the firmware of the hard disk and see what the hard disk's logs have to say about the health of your hard disk please?

If you have the right tools and technical ability you may have a spare hard disk lying around you can try swapping the hard disk for a different one and see if that helps.

If you have already been adding and removing hard disks or if you assembled this computer yourself, please check your connections. 
If you have an IDE hard disk and CDROM, please make sure you have the right jumper settings for the kind of ribbon cables  you have and the way you have the drives plugged in. This includes the CDROM drive if you have one, (I assume you do since you're able to boot a LiveCD). :)

If you have 'cable select' IDE ribbon cables, make sure the blue end is plugged into the motherboard socket and the black plug is plugged in to the drive you want to be 'master', and the grey plug goes to the drive you want to designate as 'slave'.

---

### Post by davesbrain on 2010-03-18
Bad sectors- none
Self assessment- passed
Overall assessment- disk is healthy

and all green in the attributes.


After installing the OS a second time...I carefully picked through the updates and omitted ones regarding grub and kernel.  After the selected updates (minus grub and kernel stuff), the mandatory reboot went ok.  After more than 24 hours I'm almost back to where I was.

---

### Post by ckadlubek on 2010-03-18
Im trying to setup this hdd so i can dual boot karmic and windows 7. I already partitioned and installed 7, and now im just trying to fix up my grub2.
can you elaborate this segment please  : )

"If it still doesn't work try looking in your CMOS and disabling any MBR write-protect feature you may have left enabled, it may also be called something like 'boot sector antivirus' or some other name."

i have no idea what "CMOS" or "MBR" stands for.

I keep getting 
"grub-setup: error: cannot stat /media/KARMIC/boot/grub/boot.img" 
after I type in the last command you listed.

Thanks in advance for any help!

---

### Post by Herman on 2010-03-19
[FONT=Arial][SIZE=2]> I keep getting 
"grub-setup: error: cannot stat /media/KARMIC/boot/grub/boot.img" 
after I type in the last command you listed.:D Sorry for the delayed reply.

Have you set 'KARMIC' as the label for your Ubuntu file system?

Is your Ubuntu 'KARMIC' file system mounted in /media?

> i have no idea what "CMOS" or "MBR" stands for.That's okay, the problems I was trying to help davesbrain with are probably unique to his machine and you can safely ignore that information as it probably doesn't apply to you or if it does it probably doesn't have anything to do with your particular problem.

Incidentally,  'C.M.O.S.' stands for Complimentary Metal Oxide Semiconductor', and that refers to the technology used to store your BIOS settings in your RTC/NVRAM chip, the BIOS itself being stored in a ROM chip.
To put it in simple terms, there is part of the BIOS you can't change, that's the ROM, (Read Only Memory), and there's the CMOS which we can flash with a BIOS update and we can boot into by pressing a designated key before the computer boots up and change settings for the motherboard. See [BIOS Page]("http://members.iinet.net.au/%7Eherman546/p1.html") for an example.
What I was asking davesbrain to check was this, [Turn off MBR antivirus or write protect]("http://members.iinet.net.au/%7Eherman546/p1.html#Turn_off_MBR_antivirus_or_write_protect") [/SIZE][/FONT]   [FONT=Arial][SIZE=2].

'MBR' stands for 'Master Boot Record', and it's in the first sector of most hard disks, and installing a MBR is called 'formatting' the disc. The MBR contains information about which sector each partition starts and ends in and what kind of file systems are there. A number of programs refer to the MBR's partition table for directions, including most boot loaders. Without the MBR, you would need to run special programs to search for your data which would take a long time. See [/SIZE][/FONT][FONT=Arial][SIZE=2][MBR Page]("http://members.iinet.net.au/%7Eherman546/p6.html") for more info. :)[/SIZE][/FONT]

---

### Post by ckadlubek on 2010-03-19
Oh no worries i actually just checked it

> **Herman said:**
> [FONT=Arial][SIZE=2]
Have you set 'KARMIC' as the label for your Ubuntu file system?

Is your Ubuntu 'KARMIC' file system mounted in /media?
[/SIZE][/FONT]

Yes i labeled the partition 'KARMIC'. I checked /media/KARMIC and it said the directory exists, so it definitely was mounted correctly. or at least to the best of my knowledge.

Thanks for the info about the acronyms, slowly learning my stuff haha. So any idea where I go from here?

---

### Post by isotonic_uk on 2010-03-19
I have a CLEVO laptop with Windows 7 64bit and I installed 9.10 from a CD, the install seemed to go fine but after it restarted I just get a 'grub loading' screen and it never goes to the grub menu. 

I have tried messing with all sorts of different configs on the BIOS but cannot get it to work. 

Can anyone advise on this?

---

### Post by Herman on 2010-03-19
> So any idea where I go from here?Well, the cool thing about this thread originally was to let people know they didn't need to chroot every time to re-install GRUB2 as was widely believed at the time and probably true in earlier editions of GRUB2.

I guess since this method doesn't seem to be working for it it's time to get serious with it.
Let's revert to the chroot method and chroot into your operating system, tell it who's the boss and make it do as it's told.

Here's my favorite chroot thread, the following Ubuntu Web Forums thread: [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240"), by taavikko.

**1.** Mount your Ubuntu file system, (in your Ubuntu partition).
You can use just go 'Places'-->'Removeable Media', and click on the icon representing your desired partition for mounting now in all modern versions of Ubuntu.

**2.** Check in your /media directory to find out what the name of your mount point is,
```
ls /media
```NOTE: If you have neglected to set a file system label, your file system may appear as a UUID hash instead of a user freindly name. 
To make things easier for yourself in future, see [How To Set File System Labels With GParted]("http://members.iinet.net.au/%7Eherman546/p10.html#Set_File_System_Labels_with_GParted") - recommended.

From now on, I'm going to use the word '[COLOR=Blue]mountpoint[/COLOR]' to represent whatever the name of your mountpoint is actually named in /media. Please replace the word '[COLOR=Blue]mountpoint[/COLOR]' with whatever the actual name of your own mount point is for the rest of these commands.

@ckadlubek, I know your mountpoint is 'KARMIC", but I'm also writing this for others who might also refer to this post in the future. ;)

**3. **
```
sudo mount -o bind /proc /media/[COLOR=Blue]mountpoint[/COLOR]/proc
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo mount -o bind /dev  /media/[COLOR=Blue]mountpoint[/COLOR]/dev
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo mount -o bind /dev/pts  /media/[COLOR=Blue]mountpoint[/COLOR]/dev/pts
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo mount -o bind /sys  /media/[COLOR=Blue]mountpoint[/COLOR]/sys
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo cp /etc/resolv.conf  /media/[COLOR=Blue]mountpoint[/COLOR]/etc/resolv.conf
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo chroot  /media/[COLOR=Blue]mountpoint[/COLOR] /bin/bash
``````
# grub-install /dev/sda
```NOTE: You don't need to type the hash mark, that should be already there to show you are 'root' in the operating system you just chrooted into.
WHERE: /dev/sda, (which indicates the MBR of your first hard disk), is where you want to install the code to that will make the MBR point to GRUB in your Ubuntu partition.
```
# exit
``````
sudo umount /media/[COLOR=Blue]mountpoint[/COLOR]/proc
``````
sudo umount /media/[COLOR=Blue]mountpoint[/COLOR]/dev/pts
``````
sudo umount /media/[COLOR=Blue]mountpoint[/COLOR]/dev
``````
sudo umount /media/[COLOR=Blue]mountpoint[/COLOR]
``````
exit
``` I'm sorry for putting you through such a big long list of commands, but the grub-install command should fix just about anything that could be wrong with your GRUB.
It does a lot more than the grub-setup command. The grub-install command runs a lot of other commands, including grub-setup, and it replaces all of your files in /boot/grub except grub.cfg, so if any of your GRUB files were missing or corrupt, grub-install would have replaced them with new ones for you.
The only drawback is all the extra commands you need to do in order to chroot first so you can run grub-install.
It's a good idea to learn how to chroot if you don't already know, because it can get you out of other tight situations you may encounter once in a blue moon, especially if you're like me and you like to be adventurous and try to do things with your operating system that most people wouldn't try.  :D

---

### Post by Herman on 2010-03-20
> I have a CLEVO laptop with Windows 7 64bit and I installed 9.10 from a CD, the install seemed to go fine but after it restarted I just get a 'grub loading' screen and it never goes to the grub menu. 

I have tried messing with all sorts of different configs on the BIOS but cannot get it to work. When GRUB just says 'GRUB Loading ... ', it probably means GRUB is in the MBR, but it didn't get very far looking for the other parts of itself. In other words, GRUB hasn't even loaded properly yet let alone being in a fit condition to load an operating system.

You could try chrooting and re-installing GRUB the same as I just explained above.

Another idea which would also work would be to boot your Ubuntu from a Command Line GRUB console and then fix it from within your running Ubuntu operating system. Here's a link to a web page about how to do that, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System   :D

---

### Post by ckadlubek on 2010-03-22
Thanks a lot for taking the time to help me Herman

I just got back into town and I plan to try it out when i get off work. I appreciate the step-by-step regardless of its length. And yeah probably a good thing to know how to chroot. Especially when having my luck with computers, feel like I spend more time trouble shooting than using the thing haha.

Thanks again, will post how it goes later tonight :)

---

### Post by ckadlubek on 2010-03-23
Herman it worked like a charm. And I got my dual boot setup. Now I get to trouble shoot all my windows 7 problems  : ( 

all of this just so i can play bad company 2, lol.

Thanks again though, I really appreciate the time you took to help me out, and the swiftness in which you did it :D

---

### Post by davesbrain on 2010-03-24
When I reboot it keeps saying 'Invalid Arguement' right after the mounting line.  Then a few more lines of 'can't find'.   Then the Busybox with the initramfs prompt.  Sorry I don't remember the exact wording.

Actually, the ONLY thing I can think of is my mobo has a built in Promise Technologies Ultra ATA100 controller host on board. And that is what my Ubuntu drive is plugged into.(And is set to be the boot devise in the Bios) The other drive on the main primary IDE channel are physically unplugged.

Primary master = XP (unplugged)
primary slave = empty drive for storage (also unplugged)
secondary master = cd burner
secondary slave = dvd burner
Promise controller = Ubuntu drive


This motherboard is an old Asus A7V classic with the built in extra IDE controller host.
[http://www.anandtech.com/showdoc.aspx?i=1303]("http://www.anandtech.com/showdoc.aspx?i=1303")


One operating system on one hard drive really shouldn't be THIS difficult to boot.
Sarcastically speaking...I'm not sure which is worse, XP and ALL of it's inherent problems, or Ubuntu that only boots when a perfect syzygy is happening during a lunar equinox and Mercury transit.

---

### Post by davesbrain on 2010-03-24
Well,  Gparted on the LiveCD seemed to have fixed it. (for now anyways).
Not sure what exactly it did, but it was some sort of auto fix I found.
It did do 3 distinct operations, one of which was resizing the partition.
I think it was 'Check'.

Now I'm paranoid about which upgrades, if any, i want to do.

---

### Post by davesbrain on 2010-03-27
Well, it spontaneously rebooted again, not sure what is causing that, and it went straight to the initramfs prompt.  As before, I booted up the liveCD opened up Gparted and used the 'CHECK' option on the file system partition.../dev/sda1.   It did it's thing, I closed Gparted,  rebooted just fine.   So perhaps that is an easy way for others to get back up as well.

---

### Post by Herman on 2010-03-27
> Well, it spontaneously rebooted again, not sure what is causing that
Power supply?
> I booted up the liveCD opened up Gparted and used the 'CHECK' option on the file system partition.../dev/sda1. It did it's thing, I closed Gparted, rebooted just fine. So perhaps that is an easy way for others to get back up as well.
I agree, a file system check is always a good idea, especially after a hard shut-down.

---

### Post by fwank10 on 2010-04-29
hey I have a question:

I'm attempting to dualboot W7 and Ubuntu 9.10, I did not use the LiveCD, and don't have one.  I have successfully created the new partition (hda2), (hda 1 is W7), and LVPM transferred Wubi Virtual to hda2 (created in W7, labeled karmic). restarted successfully into Ubuntu, I still had Wubi, and maybe shouldve stayed here to fix the Boot settings?....but
I went back in W7, uninstalled Wubi. Tryed to relog into Ubuntu, and my Boot manager lists unknownOS only, so i select that and it takes me directly to W7....so my WBoot Manager, and GNU GRUB menu is not loading... I had some success with earlier steps, but this is the part that has me confused the most, do I "require" the LiveCD?? to fix my GRUB2??

Anyways now I'm stuck in W7..., every indication to me is that I've made lots of progress, but now I take 2 steps back....anyone have advice?

Thanks

---

### Post by Herman on 2010-04-29
Sorry, but if you're asking me I can't help you, I have never tried wubi and I don't know anything about it.
I have read that it's a way for Windows users to try out Ubuntu without partitioning their hard disk to see if they like it enough to try installing it to hard disk in its own partition.
If you have made up your mind that you do like Ubuntu, you would need the live CD for that. There are other ways to install Ubuntu like [unetbootin]("http://unetbootin.sourceforge.net/") in case your computer doesn't have a working CD or DVD drive. You will probably find it easier to get help when you have a real Ubuntu install since it's more likely people who have the knowledge to be able to help will have experience with real Ubuntu installations. :)

---

### Post by fwank10 on 2010-04-29
i'm asking if I require the ISO Live CD, because then I need to make it. 
that means I have to burn an ISO image, which I've never done, nor has anyone that I know of....
I wasn't asking anyone in particular....but using phrases like "our ubuntu", is very condescending. It makes me angry that's for sure....
I've been using Ubuntu 9.10 with "wubi" for 3 months, it took 2 months to get online, I do like it, especially since Vista/7 are absolutely ridiculous....but I see, some choose to treat me like a stooge...

if you'd like me to make a new thread, please I need instruction, this site is confusing!!:confused:

---

### Post by Herman on 2010-04-29
> I wasn't asking anyone in particular....but using phrases like "our ubuntu", is very condescending. It makes me angry that's for sure....Please accept my most humble and profound apologies, I meant  'try **out**' ubuntu, not 'try our' Ubuntu, I was not aware of my typo until you pointed it out. The 'r' is right beside the 't' on my keyboard and I'm not much of a typist, so once, again, sorry about that. I didn't mean to be condescending at all, the alteration in meaning is entirely accidental. :oops:

I have edited my earlier post to correct it.

---

### Post by Herman on 2010-04-29
> if you'd like me to make a new thread, please I need instruction, this site is confusing!!I think your best chance of attracting the attention of someone who might know something about wubi would be far more likely to be able to find you if you do start a new thread of your own.
It's not that I wouldn't help you if I knew how, but I really do not know anything about wubi installations. 

To start a new thread of your own, you just go to the front page of any of the sub-forums here, like '[Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")', and you look for a button called 'Forum Tools', and click on that for a drop-down menu.
From there you should be able to follow the prompts easily enough.
Giving your thread a suitable title is important, one that describes your problem in a few words is usually a good idea, like 'moved wubi install to new partition - how do I boot it?', or something like that maybe.

---

### Post by Herman on 2010-04-29
> i'm asking if I require the ISO Live CD, because then I need to make it. 
that means I have to burn an ISO image, which I've never done, nor has anyone that I know of.... Well, possibly I can help you there.

You should be able to use whatever CD burning program you have to burn your .iso file to disk as an image, so it will be bootable. 
Don't let your burner program write the file as data, you will have a nice backup of your downloaded .iso file if you do, but it won't boot, (at least not the way it's supposed to), so it will be practically useless.

If the CD writing program gives you a choice of speeds to burn at, it's generally best to choose a slow speed for maximum clarity in the data. The software in the CD is highly compressed an it only takes an error as minor as a missing punctuation mark to foul up software, and the consequences of that would be unpredictable.

If you don't have any CD writing program, a nice free one I tested a long time ago that can be installed in Windows is InfraRecorder from [http://infrarecorder.sourceforge.net]("http://infrarecorder.sourceforge.net/")/, and it was only a very small download.
These instructions are old, and may be out of date, but here's what I did,
1. The package needs to be unzipped before you can do anything with it.
2 . After that, it's possible to right-click on the InfaRecorder CD icon, and click 'Open'.
3. A window opens with four panes, I just ignored those and clicked 'Actions'-->'Burn Image', and a new window, titled 'Open' appeared, showing the contents of 'My Documents'.
4.  I navigated to my downloaded .iso file.
5. Then I clicked 'Open'.
6. In the next window I selected to burn the disc at a nice slow speed, 1x, and everything else (the defaults), looked okay to me, so I clicked 'OK'.

---

### Post by fwank10 on 2010-04-29
Herman, 
I must apologize for my tone, I was a little jumpy. My question was also poorly phrased...but now having the LiveCD is good thing to have.
I made the LiveCD, got it booted, and "everything" went perfectly. 

Thanks

---

### Post by Herman on 2010-04-29
Cool, did you install Ubuntu with the Live CD? 
Or did you find a way to fix your wubi install?

---

