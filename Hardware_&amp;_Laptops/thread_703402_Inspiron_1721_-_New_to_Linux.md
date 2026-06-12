---
title: "Inspiron 1721 - New to Linux"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by AbsentHarvest on 2008-02-21
I have had this computer since summer.
Dell Inspiron 1721
2GB RAM
160GB Hard Drive
512MB Graphics
1.6 Dual Core Processors
Windows Vista Premium

I have no idea how Linux, or Ubuntu works. However, i want to give it a whirl. Where do i start? I've been hearing a lot about dual booting. This open-source OS has me excited. can anyone guide me through this?

---

### Post by sandysandy on 2008-02-21
> **AbsentHarvest said:**
> I have had this computer since summer.
Dell Inspiron 1721
2GB RAM
160GB Hard Drive
512MB Graphics
1.6 Dual Core Processors
Windows Vista Premium

I have no idea how Linux, or Ubuntu works. However, i want to give it a whirl. Where do i start? I've been hearing a lot about dual booting. This open-source OS has me excited. can anyone guide me through this?

u have come to the right place. 

first of all, do get a Ubuntu live CD either from a friend or from a magazine or download from Ubuntu website itself and burn as ISO image on CD. U can also request for free CDs on Ubuntu website.

u can boot into the live CD and get the feel of linux without even installing to hdd.

here&#347; a great link to dual booting

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

enjoy the experience

regards

---

### Post by AbsentHarvest on 2008-02-21
Alright. I'm facing one issue at the moment.

This appears to be the only Vista-Ubuntu Dual Booting tutorial.
One, can i avoid re-installing vista? I don't want to lose my programs.
Is there a way to get around this?
Also this tutorial is, " DUAL BOOT VISTA and LINUX (Ubuntu 6.06)"
will it work with the newest version?

---------------

STEPS:

< 1 >  Install Vista Beta 2 from its install DVD per the instructions below.  You are not using the 'Upgrade' option here 

from a previous installation of Windows XP.  Be sure to choose instead the 'Custom' install option -- for a clean install of 

Vista onto the hard drive.

< 2 >  When you get to the point where it asks where you want to install Vista, select the 'Advanced' option.  Create two 

partitions.  These partitions will hereafter be referred to as Partition 1 (Linux) and Partition 2 (Vista).  However, on the 

Vista install screen you are looking at right now, they will be numbered as 0 and 1 (instead of 1 and 2).

< 3 >  Click on the second partition -- Partition 2 -- and Vista will install onto that second partition.

< 4 >  After installation and before connecting to the Internet for the first time, be sure to protect your Vista 

installation with Avast! antivirus 4.7 .  Go get updates for Vista.  Restart your machine, and defrag Vista.

< 5 >  Insert the LiveCD for Ubuntu 6.06 (or Ubuntu variant) -- desktop PC - i386 version.

< 6 >  From the Ubuntu desktop, go to System --> Administration --> Disks.  Have a look at the partitions and verify that 

your Vista installation is in Partition 2.  (The file system in this partition will be Windows NTFS.)

< 7 >  Click on the 'Install It' icon on the Desktop.  When you get to the part where you can fiddle with partitions, you are 

going to play a little game of Forward/Back using the Forward and Back buttons on the dialogue box.

< 8 >  Examine the partitions it shows.  You are going to right click and select 'Delete' for any partition which does not 

contain Vista.  Don't delete Partition 2 containing Vista!  Press forward to delete those partitions.

< 9 >  Now press the Back button.  Keep deleting extraneous partitions until you have nothing but Unpartitioned Space and 

Partition 2 containing Vista.

<10 >  When all partitions except Vista (on Partition 2) are deleted, press Back a few times until you get to the beginning 

of the dialogue for partitions.  There should now be an option to install Ubuntu into a "Use the largest available space".  

Select that option, and install Ubuntu.

<11 >  Ubuntu will install into Partition 1, and will also create a Swap Partition.  These will occur physically on the drive 

before the Partition 2 - Vista install.

<12 >  Restart your machine.  The machine will boot into Linux for now.  From the Ubuntu desktop, choose the option appearing 

to download all updates for Ubuntu.  Download these and it will install them for you.

<13 >  Restart again.  At the Ubuntu desktop, we are now going to edit the GRUB menu.lst file.  GRUB is the boot loader for 

Ubuntu.  Right now, GRUB doesn't know where to look and find Vista.  A small edit of the menu.lst file will fix this.

<14 >  Select Applications --> Accessories --> Terminal from the Ubuntu desktop.  At the ~$ prompt, type this:
Type this --------> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
This will create a backup of the original menu.lst file -- a file we are now about to change.

<15 >  Again at the ~$ prompt, type this:
Now Type This ------------> sudo gedit /boot/grub/menu.lst

<16 >  Near the top of this file, you will see a command line that looks like this:
       timeout      3
       I suggest changing that '3' to a '7' (seconds).  This gives you a little more time to go into GRUB's boot menu, when 

you want to choose which OS you would like to boot.

<17 >  Near the bottom of this file, you will find a line that looks like this:
## ## End Default Options ##
And immediately below that, you will see 'title' command lines for the various Ubuntu kernel options you currently have 

available.  We are going to now add a new, small 'title' section.

<18 >  Immediately below that ## End Default Options ## line, add the following text:


title  Windows Vista Beta 2 build 5384
root  (hd0,1)
makeactive
chainloader +1


Please note you are adding this text ABOVE all other Ubuntu title mentions in the file.

<19 >  Be sure to press the 'Save' icon so that you save these changes!

<20 >  That's it.  You're done.  When you next boot the machine, don't touch a thing and it will default boot into Windows 

Vista.  Confirm this, then restart the machine again.  For this restart however, press the 'Esc' key during the 7-second 

countdown.  You will go to the GRUB boot menu where you can choose Windows Vista or the first Ubuntu kernel line.

---

### Post by sanandrikos on 2008-02-22
no you dont have to setup vista again.you just need one partition to install ubuntu to(+1 small swap partition).do u have partitions on your disk?i m not sure about grub,with xp it works automatically

---

### Post by jan quark on 2008-02-22
you can also have a look at this page

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

