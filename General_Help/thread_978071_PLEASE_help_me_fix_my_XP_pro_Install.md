---
title: "PLEASE help me fix my XP pro Install"
date: 2008-11-10
forum: General Help
---

### Post by asg808 on 2008-11-10
I've just about lost my mind over this problem. here it is:

I just bought an acer aspire one netbook w/ 120g HDD. There was XP Home on it. I wanted to try gOS and Ubuntu. Ive never used ubuntu/linux until now, but i'm an experienced xp pro user. Anyways, I had xp on 90g, ubuntu on 10g, and gOS on 10gigs. Everything worked fine until I used PArtition Magic to partition my windows 90gig drive into a 12gig system drive and the rest for storage/backup. win restarted, screwed up GRUB and I couldn't boot ANYTHING after that. GRUB 17 error. Tried to fix that problem, and ended up deleting my win partition on accident. Now I can load ubuntu, but everytme  i try to load Windows, it blue screens me right when you hit the menu to intall, repair windows. How can i fix this? I tried a live gpart program but it doesn't work. Im a noob to linux so please explain how to fix it as if you were talking to an old lady, thanks!

---

### Post by cariboo on 2008-11-10
I would suggest using partition Magic to completely wipe out any patitions you have created and use your Windows XP installation disk to create a windows partition to your specifications.

Jim

---

### Post by asg808 on 2008-11-10
I cant use Partition Magic anymore. I cant even install windows. Everytime I try to re-install windows, it blue screens me immediately after it loads the system files. I cant get to the menu screen where you can partiton/repair/reload windows. It just keeps blue screening me. I tried gparted cd made a ntfs partition, but i think the windows cant recongize the /dev language from linux. I also tried fat32, no help, still blue screens in exact same place. Help, i have to install xp today! I need a program for work!! Theres gotta be a way to fix this, i don't want to end up hating linux for this! I kinda liked ubuntu 8.04 hardy.

---

### Post by theozzlives on 2008-11-10
use gparted to wipe  all partitions and try booting from the CD

---

### Post by TeXtonyx on 2008-11-10
I've used this method in the past. Obtain a resuce disk, UBCD or
Trinity, or maybe Bootitng. Delete your MBR and rewrite it with a
standard Windows MBR. Next delete all partitions on the hard drive.
Then install XP to an entire clean drive. Then resize your drive,
shrink it so that you have some unallocated space. I now use Acronis
and I've used Partition Magic, maybe Gparted is free. After you
shrink XP, test to see that it still boots. Sometimes you can 
delete all the partitions and just install XP to say 60% of the
drive capacity, leaving the rest unallocated for Linux. This does
not always work, depends on the cd you have. Might as well try it,
if not install to the whole drive and then resize it.

Then you can use 'install to largest free space (guided)' from the
live cd if you want to. That keeps XP safe. I don't think this is
entirely a Linux problem. I had a failed SP3 update for XP, that
failed and produced a very similar sounding error. I wound up
taking the drive out, putting it into another computer as slave,
and then using Acronis to clone the primary drive to it. That
fixed the drive so that it was amenable to a cd boot install to it.

---

### Post by asg808 on 2008-11-11
removing my hdd is not an option for me. I have an Acer Netbook and it's a PITA to take apart. I wish it were easier to remove but it's complicated. If I knew what I was getting into, I wouldve never installed ubuntu. I didn't know about issues like this one. I didn't know how hard it was to reloaad winxp after and ubuntu install. GEEZE!! It's driving me nuts! I need my skype and I can't get it to work on my aspire one. It freezes my OS when i try to connect. Not too mention all my games.

---

### Post by TeXtonyx on 2008-11-11
You've already deleted your XP partition so you haven't much to lose.
Boot with a rescue cd, UBCD, etc., and delete your MBR. Replace it with
a standard MBR. You might be able to do this with a floppy, if you
have a floppy drive. Try downloading win98se from bootdisk.com 
[www.bootdisk.com/bootdisk.htm](www.bootdisk.com/bootdisk.htm) , boot, and C:\> fdisk /mbr
Put XP or win98se on a usb stick and change the bios to boot from 
it. The XP commands are fixmbr, fixboot. 

Have you tried booting with a rescue cd yet? Delete and restore
the MBR. Delete all partitions. Then try your XP cd. Another way
is to download the utility diskette from the hard drive manufacturer.
This will usually have the option of restoring the drive to a 
clean slate, as it was shipped. No floppy drive, try a usb stick. 
You can find out your hard drive model by entering the bios 
during bootup and you will have time to record the drive model#.

If you can't boot XP, learn how to do this with Ubuntu, can't boot Ubuntu,
borrow another computer to burn the disks or usb stick. Many of the
Ubuntu users are able to do XP stuff with Ubuntu, though it is more work.

[http://forum.aumha.org/viewtopic.php?f=62&t=31844](http://forum.aumha.org/viewtopic.php?f=62&t=31844) might help
[url]http://acer5051.blogspot.com/2007/09
/install-xp-pro-sp2-from-usb-2.html
[paste into one line for browser]

---

### Post by asg808 on 2008-11-11
ThanX TeX, I didn't think of trying the HDD msnufacturer rescue. Will try that tomorrow and let you guys know. Thank god I posted this, I was going nutzo

---

### Post by Aearenda on 2008-11-11
The Windows XP Aspire One comes with a recovery partition on the hard drive, and no CD. I hope you haven't deleted ALL the partitions on the drive! In the BIOS setup screen, you can go to the 'Main' tab and enable D2D recovery. It's all described in the manual that comes with the 'puter. It will probably wipe your Ubuntu installation, but that's easy to put back afterwards.

---

### Post by TeXtonyx on 2008-11-11
The Windows XP Aspire One comes with a recovery partition on the hard drive, and no CD. 

That's a good idea. Only he used Partition Magic which can see a
hidden partition so let's hope he wasn't too thorough in deleting.

1.      At the Acer splash screen, you can press Alt and F10 (at the same time you would press F2 to enter the BIOS) to bring up a DOS style version of eRecovery.

· The unit is able to reload Windows from this mode faster then from CD.

·        The password by default is 000000 (6 zeros) and it is displayed when you are asked for the password.

· Users are able to change the password in this mode for eRecovery only.

·        The system can recover from the hidden image on the hard drive (PQService partition) or from CD/DVD media.

·        It is possible to reload from the factory style CDs/DVD or the snapshots that the Windows version of eRecovery creates.

-----------------------------------------------

[http://www.aspireoneuser.com/forum/viewtopic.php?f=6&t=6368](http://www.aspireoneuser.com/forum/viewtopic.php?f=6&t=6368)
RE: Error 17
------------------------------------------------------

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

The a150s have 5400RPM Sata HDDs. Mine has a Western Digital Scorpio, but
[http://support.wdc.com/product/download.asp?level1=7&lang=en](http://support.wdc.com/product/download.asp?level1=7&lang=en)

--------------------------------------------------

I believe some have Seagate Momentus or one of the Hitachi drives in them.

---

### Post by TeXtonyx on 2008-11-11
[http://articles.techrepublic.com.com/5100-22_11-5928902.html](http://articles.techrepublic.com.com/5100-22_11-5928902.html)
How to put XP on a usb stick

---

### Post by theozzlives on 2008-11-12
After you get a "clean slate" install XP FIRST, then Ubuntu

---

### Post by asg808 on 2008-11-14
man, o, man...I just can't get this xp installed. Keeps Blue screening me. My Windows disk is fine, i know for sure. I have several copies, all BSOD in the exact same place. I guess my only option is to remove the HDD, install it in a PC and format via Partition Magic or Windows. I honestly CANT BELIEVE how much of a pain this turned out to be. It's been a week now. No skype, no Quicken, no photoshop (GIMP SUCKS THE FAT ONE). I really wanted to like Ubuntu, but it's proving to be way too much trouble for a linux newbie. I wish it were easier and more compatible with windows...at least for booting and formatting. Thanks for everyones help, I wish there was a better way to do than removing my HDD. If anyone can give me exact instructions, I'd appreciate it. Thanks!

---

### Post by Aearenda on 2008-11-14
I expect there are special drivers in the Aspire One installation that are not present on a standard XP CD. If I were you I'd be looking for someone with the exact same netbook who is willing to let you copy the hidden re-install partition off their disk drive and onto yours.

---

### Post by la3875 on 2008-11-14
I'm not sure if this will help at this point, but I have found this link and related tools invaluable when experimenting with the various installs and operating systems...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


Best of luck!

---

### Post by PocketDog on 2008-11-14
It's hardly fair to blame Ubuntu for something caused by a combination of Partition Magic and user error. Anyway, I've had problems with installing XP on a corrupt partition/drive because they didn't look to be corrupt. Acronis has been mentioned in this post already, if you have any way of burning  Acronis to a bootable flash key or USB drive then I highly recommend it - it will *properly* clean your drive, fixing any data corruption, and enable you to install XP. Good luck

---

### Post by Brandel Valico on 2008-11-14
Have to agree with Pocket Dog. It is a bit unfair to lay the blame for what amounts to user error from what I read on Ubuntu. Or XP for that matter even. Still it does seem odd that you can't wipe the drive and re-install windows. Since if you fully formatted it it should have deleted all the partitions including the Linux ones.

Have you tried a full format of the Drive?

 You can also run Skype in Ubuntu natively by the way. Not sure about Quicken and for myself Gimp works better then Photoshop. 

Another note to consider is that Ubuntu isn't a windows program so I'm curious why you feel it should be compatible with Windows.  They are two mutually exclusive OS's. Though Linux Distro's do have a lot of ways to run Windows programs the same isn't true to my knowledge the other way around. (Will have to go take a look but I don't recall a way to run .deb on windows)

---

