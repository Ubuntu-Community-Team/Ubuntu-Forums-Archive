---
title: "Dual booting XP (Ubuntu installed 1st)"
date: 2008-12-23
forum: Hardware
---

### Post by y0umebednow on 2008-12-23
i really love the new ubuntu 8.10 :)
but i still have to play my windows games so im trying to install XP Pro back into my laptop (Toshiba Satellite Pro L300-EZ1004X)

i followed this guide to do it: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

After i shrinked the ubuntu partition for XP to be installed on there, i tried booting with XP CD. After the part where it asks you to agree with the terms and condition, the partition part opens. 
**THIS** is where im stuck. for some reason there are no partitions to choose from. infact there is nothing to choose from. when i press enter, the blue screen shows up. 
i went back into ubuntu, opened gparted, and saw that there was an Exclamation mark after /dev/sda3. the warning said "unable to read content of this file system. Because of this some operations may be unavailable."

if you guys want some more detail on anything, please do ask.

Thank you!

---

### Post by cariboo on 2008-12-23
You may run into problems, because Windows wants to put it's boot files on the first partition of the first hard drive, and after you install Windows you will have to reinstall grub, as you will only be able to boot into Windows. If it isn't a lot of trouble I would wipe the hard drive clean, and install Windows first, then install Ubuntu.

The way I do it is to just partiton enough space for Windows and leave the rest of the hard drive blank, then install Ubuntu.

Jim

---

### Post by y0umebednow on 2008-12-23
i have too much to lose if i did a fresh install...

isn't there anything i can do to fix this?

i followed this guide for my desktop and it worked...
but for some reason my laptop is giving me this problem

---

### Post by logos34 on 2008-12-23
what's sda3?  Post your 

sudo fdisk -l

---

### Post by y0umebednow on 2008-12-24
sda3 is my NTFS Partition that i want to install XP on.

here is fdisk:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd468c326

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14819       18662    30876930   83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda3               1       14818   119025553+   7  HPFS/NTFS
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by logos34 on 2008-12-24
> **y0umebednow said:**
> sda3 is my NTFS Partition that i want to install XP on.


/dev/sda3               1       14818   119025553+   7  HPFS/NTFS
/

Delete that partition woth Gparted in ubuntu.  So all you have is unallocated space.  Then boot the XP cd and try the installation again--hopefully it will recognize it.  If so, make sure to do a regular format (NOT 'quick').  

As you probably know, windows will overwrite the grub bootloader, so you'll have to restore it (see link in my signature).  [Add windows entry to menu.lst.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu")

BTW, your lappy specs show it comes with 120 GB HDD (maybe you have an upgrade).  What does 

sudo lshw -C disk

show?

---

### Post by y0umebednow on 2008-12-24
after i deleted the partition, XP installation still says the same thing... This is on the partition part:
"Unknown Disk
     <There is no disk in this drive.>"

This is where i got my laptop from and it says 160 GB:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834114466](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114466)


sudo lshw -C disk :

naeem@naeem-laptop:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM UJ-850S
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.40
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk
       description: ATA Disk
       product: TOSHIBA MK1646GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: LB11
       serial: 38PBT02IT
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d468c326
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb

*This output is after deleting the partition*

Also, is there a way to open the screen resolution window without going to system > pref> screen resolution? i plugged my laptop into the tv earlier and now its resolution has changed. i cant see the top panel and my mouse continues to go right even after the screen ends.

---

### Post by logos34 on 2008-12-24
(for the resolution problem: right click on the desktop for properties, then change top panel to left side..hopefully you can then see the 'System' menu to go to> prefs>screen resolution)

Ok, Sata II drive. But what's this:

> *-disk
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sdb

blank usb flash drive? 

Go into the Bios at startup (F2, F12, Tab key, etc).  What Sata or hdd mode is it in?

---

### Post by y0umebednow on 2008-12-24
there is no "properties" when i right click on the desktop. 

i tried sudo xrandr -s 1280x800
but it says: "size 1280x800 not found in available modes" 
i dunno why... and i cant even change the visual effects to normal.

what do you mean by "What Sata or hdd mode is it in?" 
i cant find any information about the hard drive in there.

---

### Post by logos34 on 2008-12-24
> **y0umebednow said:**
> there is no "properties" when i right click on the desktop.

I guess you have to click on the panel to get to 'properties', but the problem is the panel is off screen...what about moving the cursor up offscreen and then trying to drag n drop (to the left of right side)?

> and i cant even change the visual effects to normal.

that you can get to from desktop: with cursor on empty space of desktop, right-click>select 'change desktop background'>visual effects tab


> 
what do you mean by "What Sata or hdd mode is it in?" 
i cant find any information about the hard drive in there.

I'll check the toshiba manual, back in a minute

---

### Post by logos34 on 2008-12-24
I believe this will solve the problem:

Download:

>     04-10-2008
    Driver
    HDD
    RAID
    Utility
    
[ACHI XP F6 Install Tool for Windows XP (v7.8.0.1012; 04-07-2008; 240K)]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1998675&rpn=PSLB1U&modelFilter=L300-EZ1004X&selCategory=3&selFamily=1073768667&selModel=1998675%7CPSLB1U#")

    > [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1998675&rpn=PSLB1U&modelFilter=L300-EZ1004X&selCategory=3&selFamily=1073768667&selModel=1998675%7CPSLB1U](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1998675&rpn=PSLB1U&modelFilter=L300-EZ1004X&selCategory=3&selFamily=1073768667&selModel=1998675%7CPSLB1U)

**ACHI XP F6 Install Tool for Windows XP**
Version: 	7.8.0.1012
Size: 	246,160 bytes
Posted: 	04/10/08
Released Date: 	04/07/08
Applicable Categories: 	Driver, HDD, RAID, Utility
Operating System: 	Windows XP, Windows XP SP2
Package: 	WinZIP Self-extracting ZIP file runs SETUP when extraction is complete. Can also be unZIPped using PKUnZip 2.04g or equivalent. See README file for installation/usage instructions.
File: 	driver_ahci_install_27415A.exe
  	Download Now
 
Description
Detailed Instructions for installing the Intel(R) Matrix Storage Manager Driver on a fresh hard drive =================================================
1. Copy the contents of this archive onto a floppy disk, CD, DVD, or USB flash drive onto the root.
2. Insert your Microsoft Windows XP Bootable CD and your floppy disk or USB flash drive.
(If you haev a CD or DVD, you will have to insert after step 6 below)
3. Power on your computer and press F12 to display the boot menu.
4. Choose the option to boot from the CD/DVD drive.
5. For **Windows XP** or later operating systems:

- At the beginning of the operating system installation, press F6 to install a third party SCSI or RAID driver.

- When prompted, select 'S' to Specify Additional Device.

- Continue to step 7.

6. For Windows Vista:

- During the operating system installation, after selecting the location to install Vista, click Load Driver to install a third party SCSI or RAID driver.

7. When prompted, insert the media (floppy, CD/DVD or USB) you created in step 2 and press Enter.

8. At this point you should be presented with a selection for one of the following depending on your hardware version and configuration:

- Intel(R) 82801IR/IO SATA RAID Controller (Desktop ICH9R)
- Intel(R) 82801IR/IO SATA AHCI Controller (Desktop ICH9R)
- Intel(R) 82801HEM SATA RAID Controller (Mobile ICH8M-E)
- Intel(R) 82801HEM SATA AHCI Controller (Mobile ICH8M-E)
- Intel(R) 82801HBM SATA AHCI Controller (Mobile ICH8M)
- Intel(R) 82801HR/HH/HO SATA RAID Controller (Desktop ICH8R)
- Intel(R) 82801HR/HH/HO SATA AHCI Controller (Desktop ICH8R)
- Intel(R) 631xESB/632xESB SATA RAID Controller (Workstation ESB2)
- Intel(R) 82801GHM SATA RAID Controller (Mobile ICH7RM)
- Intel(R) 82801GBM SATA AHCI Controller (Mobile ICH7M)
- Intel(R) 82801GR/GH SATA RAID Controller (Desktop ICH7R/DH)
- Intel(R) 82801GR/GH SATA AHCI Controller (Desktop ICH7R/DH)

9. Highlight
- Intel(R) 82801HEM SATA AHCI Controller (Mobile ICH8M-E) hardware in your system and press Enter.

10. Press Enter again to continue. Leave the floppy disk in the system until the next reboot as the software will need to be copied from the floppy disk again when setup is copying files.
 
Applicable Models:
Satellite Pro L300-EZ1004X, L300-EZ1005X, L300-EZ1004V, L300-EZ1005V, L300-SP5803, L300-SP5801, L350-S1001X, L350-S1001V


Basically, the problem is XP (unlike vista and ubuntu) does not come with sata drivers, so if (as in your case, apparently) you installed linux in Sata mode AHCI (which supports Sata II features like hot-plug, NCQ, etc), and then try to install XP, the latter will be unable to recognize the hard disk until you insert the drivers or else change to IDE compatibility mode

---

### Post by y0umebednow on 2008-12-24
ah a hope! thank you so much.

"1. Copy the contents of this archive onto a floppy disk, CD, DVD, or USB flash drive onto the root."

Okay so ill copy the extracted files onto a USB, but what does "onto the root" mean? where exactly is that?

i understand the rest of the steps fine. 

once again thank you!!

---

### Post by theozzlives on 2008-12-24
if you have a SATA drive, Windows XP don't support it you'll have to change it to ATA in your CMOS setup. I had that prob installing Dual Boot after the fact on my laptop.

---

### Post by logos34 on 2008-12-24
> **y0umebednow said:**
> 
Okay so ill copy the extracted files onto a USB, but what does "onto the root" mean? where exactly is that?

meaning, don't put them inside another folder...just put them in the base directory.  i.e. if the usb is mounted at '/media/disk', then copy files there

---

### Post by y0umebednow on 2008-12-24
Okay for some reason when i press F6, nothing happens. it just skips it and goes to loading windows files.

any suggestions?

---

### Post by y0umebednow on 2008-12-24
Ok never mind. after loading the files i was prompted to select 'S' to Specify Additional Device. But after i did that, it says "Setup could not find a floppy drive on your machine to load OEM drivers from floppy disk"

is it not reading the USB?


EDIT: i also burned the files on a CD. and after inserting the CD and pressing S, it still gave me the same error. 

why is it only looking for a floppy drive? my laptop does not even have a floppy drive =/

---

### Post by logos34 on 2008-12-24
what a pain in the a** M$ is...i've never looked backed since I ditched it

i'm thinking that xp does not have usb drivers loaded at startup to enable you to access the flash drive, it can only do floppy (vista probably can though).  However, the instructions above sure give the impression you CAN use cd or usb

I think you're only options at this point are:

a. 'slipstream' the sata and other drivers into a new XP install CD image (but then you'd need to do it on a machine running XP):

[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1)
(->step 3)
[http://www.maximumpc.com/article/howtos/how_to_slipstream_windows_xp_sp3_and_vista_sp1](http://www.maximumpc.com/article/howtos/how_to_slipstream_windows_xp_sp3_and_vista_sp1)

b. install windows in IDE compatibility or legacy mode, and resign yourself to swtiching between the two modes when you want to bootthe other OS

c.  Reinstall XP with the disk in IDE mode.  Then ubuntu. [edited--got order backwards]  You can backup your pkgs and updates so you don't have to redownload them all.  You might even try cloning ubuntu back onto the disk after you change the sata mode--save you installation time if it works, (never tried it).

---

### Post by y0umebednow on 2008-12-24
Holy ______ ______!!!! wow i dont think ive ever been so fraustrated...

what would the easiest way to install XP on my laptop? 
at this point i really dont care about losing ubuntu. i can always install it again and it doesnt take an hour to install unlike XP...

how would i go about doing step one? i have XP installed on my desktop. how would i add the drivers AND the XP install CD image in ONE CD?


EDIT: what is Nlite? can it help me install XP?

---

### Post by logos34 on 2008-12-24
> **y0umebednow said:**
> 
what would the easiest way to install XP on my laptop? 
at this point i really dont care about losing ubuntu. i can always install it again and it doesnt take an hour to install unlike XP...


option c.

From what i've read you won't even notice the difference, especially for average everday computing.   

Set the Bios for sata ide compatibility mode or whatever name it goes by on Toshiba machines. Install XP Pro first.  Then reinstall ubuntu because you want grub to overwrite the windows bootloader.  

As I said you can backup your installed deb pkgs (/var/cache/apt/archives) to save you download time.

> **y0umebednow said:**
> 
how would i go about doing step one? i have XP installed on my desktop. how would i add the drivers AND the XP install CD image in ONE CD?

EDIT: what is Nlite? can it help me install XP?

Those guides are aimed at users who are working from the same system/machine they want to make the image for...it's different if you're doing it on another machine (let alone a desktop vs. notebook).  NLite is the freeware that you use to make the cd with the drivers   and patches compiled in.  I think I have a link somehwere to another way to do it...I look for it if you're interested, but I really think you're better off reinstalling in IDE mode, less hassle.

---

### Post by logos34 on 2008-12-24
here's the main one I had bookmarked:

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

yopu could do it on your desktop

So basically, try the method in the softpedia link above...All you're doing is essentially adding the ahci drivers to the XP Pro install cd, integrating it into a new image, burning it to a new custom install CD.

If that doesn't work, then try option c

---

### Post by y0umebednow on 2008-12-24
alright im going to try the softpedia link. if that doesnt work then fresh install it is.

thanks for all your help, i really appreciate it!

the options for SATA are "AHCI" and "compatibility"
so im guessing i would have to change AHCI to compatibility?

---

### Post by logos34 on 2008-12-24
> **y0umebednow said:**
> alright im going to try the softpedia link. if that doesnt work then fresh install it is.

thanks for all your help, i really appreciate it!

my pleasure! Helps improve my troubleshooting skills.  Besides, I'm particularly interested in this issue--there's been a noticeable uptick in the number of posts about it from dual-booters, probably because most new computers come with Sata II/3.0 GB/s (which require AHCI for certain features like advanced powersaving, native command cueing, and hot-swap, etc)...either that or people are replacing old drives with sata.   

> the options for SATA are "AHCI" and "compatibility"
so im guessing i would have to change AHCI to compatibility?
yes, 'compatibility'

---

