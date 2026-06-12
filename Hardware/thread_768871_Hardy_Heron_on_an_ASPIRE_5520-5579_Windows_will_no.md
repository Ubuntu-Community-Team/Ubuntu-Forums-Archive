---
title: "Hardy Heron on an ASPIRE 5520-5579 Windows will not boot but fixed wireless and video"
date: 2008-04-26
forum: Hardware
---

### Post by austin183 on 2008-04-26
UPDATE:  Now I reinstalled windows, then I reinstalled Ubuntu, and now I get a "NTLoader missing" error when I try to boot into Windows.Hi everyone.



SECOND UPDATE:  OK, now everything boots correctly, and I have drivers for everything in Windows and Ubuntu!



**I think altogether I spent 9 hours on this, and that's just way too long for an average joe.  There needs to be something in place that handles this problem.**



I was missing my NTLDR, NTDetect, and boot.ini file from my windows partition.  I found a useful microsoft knowledgebase article here



[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)



It says that I should take the ntldr and ntdetect files from the Windows Installer CD.  It was talking about Windows 2000, but same difference.



I didn't want to go through the Windows Installer's recovery interface.  So I copied the files from the windows cd using Ubuntu graphically.



And I wrote the boot.ini file using Gedit.



I ran 



$ sudo fdisk -lu



to find out which partition my Windows installation was using.
  Here is what I got:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dae76f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+   7  HPFS/NTFS
/dev/sda2   *    20466873   254694509   117113818+   7  HPFS/NTFS
/dev/sda3       254694510   264462029     4883760    f  W95 Ext'd (LBA)
/dev/sda4       264462093   488392064   111964986   83  Linux
/dev/sda5       254694573   264462029     4883728+  82  Linux swap / Solaris

So my Windows inst
all is on /dev/sda2


So my boot.ini file looks like this:

{{{{

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

}}}}



And my grub menut.lst entry looks like this:



{{{{

# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows XP

root		(hd0,1)

savedefault

makeactive

chainloader	+1

}}}}

So now everything works, and I can watch The Office wirelessly in either Windows and Ubuntu!

END UPDATE


Hi everyone.

I just installed Hardy Heron (Ubuntu 8.04) on my almost brand new Aspire 5520, and at first my Nvidia 7000M card did not work, and my Atheros AR5BXB63 wireless card was not recognized.

This sucked, so I tried to boot back into Windows XP so I could research the situation.  But I could not boot back into XP!

At first Windows XP was not recognized in the Grub menu.  So I tried to add it to 

/boot/grub/menu.lst

by opening a terminal and typing

$ cp /boot/grub/menu.lst /home/austin/Desktop/menu.lst

$ sudo gedit /boot/grub/menu.lst

and I added the following lines in the following context

{{{{### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#{{{{This is what I added}}}}
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

[[END OF FILEL]]}}}




And I got my (hd0,1) entry by running "sudo fdisk -lu"

And getting

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dae76f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+   7  HPFS/NTFS
/dev/sda2   *    20466873   254694509   117113818+   7  HPFS/NTFS
/dev/sda3       254694510   488392064   116848777+   f  W95 Ext'd (LBA)
/dev/sda5       254694573   264462029     4883728+  82  Linux swap / Solaris
/dev/sda6       264462093   488392064   111964986   83  Linux

I figure /dev/sda2 is my Windows XP file.

But I don't know where the /dev/sda3 entry came from...  I looks like it thinks my linux partitions are some phunky windows partition ...?

This may have happened after I opened the recovery console from a Windows XP install CD and I ran the following commands

> fixmbr

> fixboot

> bootcfg /rebuild

> chckdsk /r

And rebooting.  When I rebooted, I got a "disk read error Press Ctrl-Alt-Delete" message.  So then I had to set up GRUB again to boot into Ubuntu, which I did by reformatting and reinstalling ubuntu on /dev/sda6.


Then I decided to solve my Nvidia and Atheros drivers issues because it was getting annoying moving to my room for cds and then the game room for the ethernet cable.  These two were pretty quick.

First, I turned off all the "Restricted Drivers" in use by going to System > Administration > Hardware Drivers.  I unchecked the Nvidia driver, the Atheros Hardware Access Layer (HAL), and the Support for Atheros 802.11 wireless LAN cards.

Then I tackled the Nvidia driver.  I read in a forum about a program called Envy which detects your video card and downloads the proper driver for it.  In order to download envy, I had to enabe the universe and multiverse repositories.

So I typed this into the terminal window:

$ cp /etc/apt/sources.lst /home/austin/Desktop/sources.lst

$ sudo gedit /etc/apt/sources.lst

and I made it look like the following

{{{{
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
}}}}

Then when I ran 

$  sudo apt-get update

my Restricted Drivers notification popped up telling me I could install some drivers.  I checked it out, and the Nvidia driver name had changed.  So I Enabled that, and it downloaded and installed the driver.  I rebooted, and I had a full 1280x800 screen with slick gui effects!

So I skipped Envy.

Next up was the wireless driver.  I spent a few minutes wandering forums in search of "Acer InviLink ubuntu drivers".  I happened upon a post where someone asked someone else what model of Atheros card they were using and that it was printed on the back of the computer.  I hadn't thought of that!  So I looked, and I saw that it was an 

Atheros AR5BXB63

So I refined my google search to "ubuntu wireless "Atheros AR5BXB63"".  The forums said I need to use the XP driver with ndiswrapper.  Luckily I had the XP drivers on my backup drive from when I upgraded from Vista to XP a month ago.  

So I installed the graphical ndiswrapper module like this

$ sudo apt-get install ndisgtk

I launched the program by going to System > Administration > Windows Wireless Drivers.

I chose to Install a new driver, and I navigated to the XP-x32/net5211.inf file in my driver folder.  The program showed that it installed successfully, but then the whole system froze.  I manually turned off the computer and turned it back on expecting the worst.  But when I booted back up, I could choose my wireless networks from my network icon on the top Gnome panel!  

So now Ubuntu works perfectly!

But my computer still works imperfectly because I still cannot boot into Windows.  I do programming for work in Microsoft SQL Server 2005 and Access 2003/7, and I need Windows on here for that reason.  I really do not want to reformat and reinstall Windows because I know it is already sitting there waiting for me to solve this puzzle.

And that is where I am stuck.  I hope that my driver experiences helps out some other Ubuntu users with an ASPIRE 5520-5579 laptop.  It really is a nice laptop.

If you have any suggestions about the Windows "disk read error" issue or can point me in the right direction by way of forum links or boot recovery tools, I would appreciate it.

---

