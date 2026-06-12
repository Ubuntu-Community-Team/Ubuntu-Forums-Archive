---
title: "Hard drive problem"
date: 2011-05-27
forum: Hardware
---

### Post by mikelisak on 2011-05-27
I have a 2.0 TB Caviar Green WD Hard Drive that I've been trying to fix for days now. It used to be partitioned with Windows but now I am running Ubuntu 11.04 on my desktop. I have tried everything from chkdsk to linux's TestDisk and Disk Utility. In all cases I have been unable to get the drive to work. Sometimes it wont even be recognized. I tried to format it in Ubuntu with Disk Utility and got this error: 

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error

Is this a hardware problem, or is there still hope to get my data back? I had a lot of important data on there and it would be really nice to get it back.

---

### Post by ILoveYorkies on 2011-05-27
> **mikelisak said:**
> I have a 2.0 TB Caviar Green WD Hard Drive that I've been trying to fix for days now. It used to be partitioned with Windows but now I am running Ubuntu 11.04 on my desktop. I have tried everything from chkdsk to linux's TestDisk and Disk Utility. In all cases I have been unable to get the drive to work. Sometimes it wont even be recognized. I tried to format it in Ubuntu with Disk Utility and got this error: 

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error

Is this a hardware problem, or is there still hope to get my data back? I had a lot of important data on there and it would be really nice to get it back.
Hi,
I wish I could help you more but I'm not a tech expert in Windows and I'm new to Linux. But if you want to try recover data on that drive then DO NOT TRY TO FORMAT OR PARTITION THE DRIVE. That will only make it HARDER TO RECOVER YOUR DATA! 
IMPORTANT QUESTIONS: What version of Windows did you have?  Is the drive an extra internal one or an external one such as usb? Was the drive working in Windows up to the time you installed 11.04 or were you having trouble with it before that? How did you install 11.04? Dual boot with Windows or inside Windows (WUBI install) or did you replace Windows completely with Ubuntu? The answers to these questions will help the experts here to figure out what you could try. In the meantime, my suggestion is to  NOT FORMAT IT, and READ as much as you can about recovering files with Windows if you still have access to it and Linux only software if you don't have access to Windows anymore.  Here is an example for Linux only version  of Ultimate Boot Disk CD or UBCD  [http://www.ultimatebootcd.com/forums/viewtopic.php?f=13&t=2771&sid=885cbf964a0025d48e04824c68fb7ef2u](http://www.ultimatebootcd.com/forums/viewtopic.php?f=13&t=2771&sid=885cbf964a0025d48e04824c68fb7ef2u) the homepage is here : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)  Here it is for the Windows version: [http://www.ubcd4win.com/ubcd4win.htm](http://www.ubcd4win.com/ubcd4win.htm)
There are others of course, I can't help you much with them since I've never had to use any yet although I did download one called SystemRescue (repairs both Win and Linux) just in case I can't reinstall Windows to the computers that I want to wipe then sell. But I haven't used it yet just made sure the livecd of it I made booted which it did. 
 I found this list at [http://en.wikipedia.org/wiki/List_of_LiveDistros](http://en.wikipedia.org/wiki/List_of_LiveDistros)
**Rescue and repair live CDs**

 
[LIST]
[*][Billix]("http://en.wikipedia.org/wiki/Billix")  &#8211; a multiboot distribution and system administration toolkit with the  ability to install any of the included Linux distributions
[*][BootMed]("http://www.bootmed.com/") &#8211; a Live CD that was made to help those not familiar with Linux repair or recover their Windows Computer from a Live CD.
[*][Inquisitor]("http://en.wikipedia.org/wiki/Inquisitor_%28hardware_testing_software%29") &#8211; Linux-based hardware diagnostics, stress testing and benchmarking Live CD
[*][Parted Magic]("http://en.wikipedia.org/w/index.php?title=Parted_Magic&action=edit&redlink=1")
[*][RIP: (R)ecovery (I)s (P)ossible]("http://en.wikipedia.org/wiki/Recovery_Is_Possible") is a Linux-based CD with partition tool and network tools ([Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29")), based on the 2.6.17 kernel.
[*][System Folder]("http://en.wikipedia.org/wiki/System_Folder") of [Mac OS]("http://en.wikipedia.org/wiki/Mac_OS") on a [CD]("http://en.wikipedia.org/wiki/Compact_Disc") or on a [floppy disk]("http://en.wikipedia.org/wiki/Floppy_disk") &#8211; works on any media readable by [68k]("http://en.wikipedia.org/wiki/68k") or [PowerPC]("http://en.wikipedia.org/wiki/PowerPC") Macintosh computers.
[*][SystemRescueCD]("http://en.wikipedia.org/wiki/SystemRescueCD") is a Linux-based CD with tools for Windows and Linux repairs, based on the 2.6 kernel.
[*][Trinity Rescue Kit]("http://en.wikipedia.org/wiki/Trinity_Rescue_Kit") &#8211; Mandriva Linux-based CD for use on a Windows or Linux-based system.
[/LIST]
I hope these websites and suggestions I've listed help while you want for an answer from a Linux expert. Good Luck.

---

