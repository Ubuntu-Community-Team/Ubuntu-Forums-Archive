---
title: "removing ubuntu"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by bobkny on 2009-04-08
Just installed 64 bit Ubuntu 8.4 as a dual boot on my 64 bit Media server PC with Windows XP. The system uses a wireless keyboard. The OS selection screen does not respond to the wireless keyboard up and down arrow keys required for OS boot selection. Other than plugging in a wired keyboard - which is an unacceptable long term solution- how can I chose which OS to boot. This will be an Ubuntu killer for me, if I can't fix.

---

### Post by bobkny on 2009-04-08
Just installed 64 bit Ubuntu 8.10 as a dual boot with Windows XP on my PC Media server. Due to some serious dual booting issues, I will likely have to remove Ubuntu, and restore XP as the only OS. Is there any way I can do this without totally reformatting my disk and re-installing XP? I was hoping that I could somehow use the partition manager on my installation CD to remove 8.10 and restore the XP partition to 100% of the disk.

---

### Post by TomErwin on 2009-04-08
That's a heartbreak to hear you are going back to the oppressors.
I am not an expert, but why don't you try to mention the issues you have with your dualbooting thing. and maybe they can find a solution here?
If not, why don't you install XP and tell it not to format? (leave data, no changes?).
or is it the type of the drive keeping you from that? sorry I am a beginner myself. 
Good luck

---

### Post by linux_lover69 on 2009-04-08
Use the live cd to format your ubuntu installation, then resize the windows partition to use the whole harddrive, then to get the bootloader to work put your xp installation disk in and repair your xp installation(you'll have to reinstall the updates, but all your programs, and things will still be there.)

---

### Post by upchucky on 2009-04-08
your dual booting issues can be fixed with this,

Get Supergrub to set up/repair Grub here:

Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

if you still want to go back to windows, download gparted. it is a bootable partitioner that will let you delete the ubuntu partition and grow the windows partition to again occupy the entire disk, or better yet create a ntfs partition as a storage partition for windows to use as a place to put user files, that way they will be safe is windows is again taken down by malware or it slowly self destructs as it is designed to do. you will need to restore the windows MBR to be able to boot windows when you remove the ubuntu partition. this is how to do it if you do not have the windows install cd that has the fixmbr utility on it.

Restore windows MBR using Ubuntu


HOW TO: Recover Windows MBR using Ubuntu LIVE CD
Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

Before the first step:
(I needed to enable the 'universe' repository (System->Administration->Software Sources) before I could install the ms-sys package. I also needed to put "sudo" in front of the ms-sys command (e.g. "sudo ms-sys --mbr /dev/sda") otherwise I got permission denied.)

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal:

sudo apt-get install ms-sys

then

ms-sys --mbr /dev/hdX

NOTE: in my case the main windows xp system is located in hda1 so I used

sudo ms-sys --mbr /dev/hda

***
ubuntu@ubuntu:~$ sudo ms-sys --mbr /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda


If you do have the win install cd it has a utility called fixmbr to restore the mbr to boot windows you will have to search on google how to do it.

sad to see you give up so easy, the dual boot problems are usually a 5 minute fix if you understand what has happened and post the right info here for us to help.

good luck.

---

### Post by ytsejam1138 on 2009-04-08
I'm assuming you have a USB dongle for your wireless keyboard.  Check the settings in your BIOS to make sure that "Legacy USB Support" is turned on. On some boards this option is also called "USB Keyboard support".  Also, make sure the USB dongle is not plugged into a hub.

---

### Post by bobkny on 2009-04-08
Thanks for the help. Update BIOS worked. Still needed an old wired keyboard however, to initiate set-up from splash screen. Wireless keyboard now functioning. Phew! I can put that old dusty keyboard back in the attic. Now onto other issues with screen resolution for my HD TV.

---

### Post by bobkny on 2009-04-08
Thanks for all of the help and suggestions. Fortunately, thanks to the help on another issue - dual boot with a wireless keyboard- I was able to fix the problem, and hopefully wont ever have to remove Ubuntu from this system. Phew! Now on to some more interesting problems like how to get the proper resolution and aspect ration for my 52" HD TV.

---

### Post by upchucky on 2009-04-09
i had to edit my post, the link to supergrub was broken, i changed it to the actual supergrub site.

---

