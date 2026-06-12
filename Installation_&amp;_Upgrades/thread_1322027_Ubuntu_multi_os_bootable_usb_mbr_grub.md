---
title: "Ubuntu multi os bootable usb mbr grub"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by iamawhore on 2009-11-10
Help create a bootable USB/MBR/Grub. 
Attempting to multiboot on an IBM model z60t. Currently the only OS installed is the Netbook Remix version of Dell/Cannonical Ubuntu 8.04 +LTS, it will remain the primary OS, it will be shared with Windows XP Home, Windows XP Professional, and OS X 10.5. 

Problem: both, the currently installed OS and XP want to own the Hardware (HDD). 

Solution: an Ubuntu bootable MBR/Grub on an external device (i.e. USB-MicroSD Card, yes it would have to be supported in the BIOS of the computer) that will boot any of the OS's mentioned in order to Fix/Install the MBR/Grub when destroyed.
Good as a backup after all is running, and very useful while in the process of multi OS installing. 

Have looked into options: 1.System Commander types. 2.Windows MBR fix 3.Live CD's -Linux Distributions with Command Line Have also looked into how to create a bootable usb device with only the MBR/Grub. (excuse if using terminolgy improperly). 

There are several blogs, tutorials, step by step for other distributions and even for Ubuntu (other versions), but none simple to understand for a newbie and particularly because only want to use the currently installed OS DVD-Rom Recovery Media, the OS itself (terminal), and no internet. 

Have all the hardware necessary. The hard drive has been partitioned to allow for other OS's. Two problems after partitioning. 1. an error messgae upon the desktop startup (The panel encountered a problem while loading "OAFIID:Desbar_Applet"). 2. the mbr bootup is slightly stalled, so slight the white text is undescernible. Not concerned with particulars at the moment. Infact, there are several drivers needed for the z60t.Hope to 'as a matter of fact' be able to solve problem 2 with the real problem help is being seeked for. 

How to (using only mentioned tools) simply, step by step create a bootable USB device (thumb drive/stick/dongle/hard drive, whatever other name given to the device) that will boot into installed version of ubuntu to then be able to use the terminal to keep/edit the MBR/Grub . 
Keep in mind windows will delete the mbr and the recovery media for the installed OS will wipe out windows and the partitions set for other OS's. 

Also, please take your time that others may succeed at this or similar. After all, its just a matter of principles here.

---

### Post by quixote on 2009-11-11
What you want to do is pretty complex.  1) A multiboot that includes Mac OSX, requires rEFIt, which runs before grub, and lets you choose OSX or everything else.  Then grub handles the "everything else" for you.  2) Windows always needs to feel it's the only thing on the disk.  If it's not happy, you may need to fix the Master Boot Record and rebuild grub.  Both are pretty easy to do. (For fixmbr you need bootable Windows media, a CD, a thumbdrive, even an old DOS floppy!, boot into the recovery console, and type "fixmbr" (no quotes) at the command line.)

Instructions about rEFIt and multibooting MacOSX: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)  There's a lot of info there, including toward the bottom multiboot systems with Windows.

Dealing with grub: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) , [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Installing to a USB drive or memory stick became a lot easier with Jaunty.  There it's just a menu option under System > Administration.  If there's a reason you'd rather stick with Hardy, this is an oldish link that could be useful: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by iamawhore on 2009-11-11
thanks for your response, and leads.
will review and get back to you. currently I just want to back up the mbr of the only os installed [(Hardy), as the install dvd-rom is unable but to do a complete 'fresh' re-install, no option to use command line] to a usb thumb drive, so that when windows installs (destroys) the GRUB, it can be recovered.
Will be using the terminal (dd command), but still trying to figure it out. reminder, don't want to use internet, nor gui/programs not included in the install disks, in part for learning, in part for those out there with limited resources. no worries regarding Windows install discs, have them (Home and Pro), also OSX discs (licese/COA not a problem for any). OSX is way down the road. will get there. By then hope to have a good step by step for dual (Windows) booting without internet, nor third party tools (OS install discs excluded). Thanks for your help.

---

### Post by efflandt on 2009-11-11
There is an Ubuntu package called mbr that can install an mbr (either its own generic one, or one from a file).  The actual binary and man page is install-mbr.  I don't think it can save an mbr to a file, but the mbr is the first 512 bytes of a disk (before any partitions), so you could copy that to a file with dd.  [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by iamawhore on 2009-11-12
efflandt: thanks i'll try it.
i'm assuming that it can be done with the current installed os alone,

(quixote: want to stick with 8.04 Dell/Cannonical version, unless the latest version is available for the mini 9, checked and the latest 9.04 titled a developers version because not yet bullet proof has been tested with the mini 10, missing drivers, etc. for mini 9 so until then, sticking with 8.04. thanks.),

or with the recovery dvd-rom in the optical drive. unable to use the dvd-rom as a live cd/dvd to use the terminal. (available for access is a Dell Mini 9, one of which has Ubuntu 8.04, the other which has Windows XP Home).

will make time to try this and post outcome.

thanks for the link.

---

### Post by iamawhore on 2009-11-17
Lost patience, but continuing the pursuit. Ran into a site that mentioned that the version of Ubuntu 8.04 +LTS that is provided by dell/canonical is not meant for dual booting, the regular version should be used. "regular"? Question, is it possible? Is it more like Windows than Linux?, I.e. disallowing a multi boot? (Accept apology for not trying the install-mbr, rather I did, but gave up easily.) Here's what happened. Formatted a 4Gb usb thumb drive using the terminal following (forgot to note author) a blog, (Will trace and post). Then, in the terminal, as root user, did a "dd if=/dev/sdb1.boot.mbr of=/dev/sda2 bs=512 count=1", here /dev/sdb1 is the usb thumb drive. As mentioned, the confirmation text in the terminal was not written down for posting here, should've/could've/would've, as patience was lost. Semi-sure the mbr was backed up, carried on to install Windows XP Home, ofcourse the ubuntu mbr was superceded. Now the computer boots by default in to Windows. Can the Ubuntu mbr be repaired using the Dell/Canonical Recovery Media DVD-Rom, or the 'supposed' backup on the usb thumb drive? A terminal is needed,correct? The DVD Recovery prompts a complete Reinstall, no option for live/recovery mode, furthermore, continuing by typing in "proceed" deletes everything on the hard drive, partitions included. What is wrong?

---

