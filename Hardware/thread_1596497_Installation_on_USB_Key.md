---
title: "Installation on USB Key"
date: 2010-10-14
forum: Hardware
---

### Post by Sylslay on 2010-10-14
Try install linux on USB Device, No sucess so far.
I try Ubuntu as well.
Looks like grub is not instaled in MBR.

I checked with fiew options during installation, 
changed sdb to sdb1 in Advandce Option,

Tryed as well diffret partition
1. Full Automatic
2. Swap plus ext4
3 Swap, plug 1gb fat16 and than ex4
4. 200mb for ext2 fot /boot partiton, than sawap plus ext4.

Still has no grub in MBR,

Any one know how instatll syslinux or lilo to that usb steak, 
at the moment just can't boot from it,

Thx in advance, 

PS.PC has moded bios for usb boot to choice on startup, but that USB key is not working on laptop (with orginal bios and option boot from  portable device),

LIVE USB works ok!!!(but only when I have one fat32 partiton)
When is made under windows or ubnutu. If I share usb to 2 or 3 partiton than neither works LIVEUSB or linux instaled on first partiton. This is when I don't have MBR in usb!!!

ANY CLUE?
PS2 In Bios I have only APM power managment and LIVEUSB work correct only with usbhub (4:1 or any hub), but when I plug it direct to usb laptop I usualy get APCI 2k XYZ error, where XYZ={0-9} and LIVEUSB STOP, and have the same error on some toshiba usb-hdd,

it's old Siemens Amilo laptop.

---

### Post by C.S.Cameron on 2010-10-14
Following is for 10.04, 10.10 is similar:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by Sylslay on 2010-10-14
Thanks :popcorn:

I will print this out and give a tray.

THX for answering.

Doesn't works.
Have 4 partiton set as above, but sitll no GRUB in MBR!!!
Meaby something wrong with my laptop.

BuT LiveUSB works ok.

Used latest 10.10 with new installer.

---

### Post by Sylslay on 2010-11-03
Sorry for not edit my above thread, 
but since time pass, I solve the problem with USB installation

!!!IT WORKS, I blame my old hardware and BIOS.
Too many laptops and mobo around. And it BIOS don't boot correctly with grub2 from usb-drive.

In past weeks, after houer's I used fiew different distros,
Ubunt10.10, Ubuntu10.04, PC-linux and Slax.


THX to google, I found this:

[CENTER][SIZE="3"]_plop_bootmanager_[/SIZE][/CENTER]

I burn ISO to CDROM, boot first from CD, than from menu of plop_bootmanager 

I choose USB to boot, and it booting grub on sd_ usb partiton

So just installed Linux Mint LDME, and works great from 8gb usb steak.

And thx to plop_bootmanager, that linux run from 2001 old mobos and laptop without usb menu in bios.
:guitar:

Ps1. Probably I may install syslinux, but this was easy-way :-)

Ps2. 40second to boot (from grub to gnome )on celeron2500 intel 845g and usb2.0[COLOR="Black"][CENTER][SIZE="3"][/SIZE][/CENTER][/COLOR]

Partitions on USB key are:

primary : 1.3-2 GB fat32 (for windows apps, books, mp3, movies etc)
primary : 5.8 -6 GB ext4 (linux / partiton )
rest of 8gb for swap, but OS booted from usb key use only 200MB-400MB ram, 600 of 1024 is steal free.

I have aobut 2.5gb free on ext4 partition for 'user' files and updates - rolling distro.

Installed grub to the root of the usb, example sdb, sdc, 

THX for all

PS3
Found today at 10th november:
that yesterday I run command under ubuntu (my main os):

sudo os-prober
sudo update grub2

a the time I had connected usb key to laptop.

and that command add entry to my deflud grub installed to MBR of sda1

It seprouse me, that I load my os-usb from entry at deflout grub, 
so I no need use any more F8/F12 command to boot from BIOS level

Grub on sda1 and sb2 does the job :-)

---

