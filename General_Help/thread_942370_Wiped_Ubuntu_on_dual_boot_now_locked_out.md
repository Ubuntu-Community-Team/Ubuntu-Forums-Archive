---
title: "Wiped Ubuntu on dual boot now locked out"
date: 2008-10-09
forum: General Help
---

### Post by quilgar on 2008-10-09
New to Ubuntu, dual booting, and anything other than simply running programmes in xp. 

I have two drives 160gig with xp, 500gig that had Ubuntu on it. Wiped Ubuntu off 500gig, partitioned it 400 and 100 then loaded data onto 400 partition. On reboot I am locked out at the grub. 

What I want to achieve is to load Ubuntu on the 100 partition without blowing the data on the 400 partition but first I have to be able to boot my machine.

Have a live Hardy disc.

Would appreciate any help to get myself back in the game. Unwilling to go it alone and risk making a bad job worse.

Not had enough experience of Ubuntu to pass comment but on xp I run Firefox, Thunderbird, OpenOffice, Audacity and other open source software so not likely to see much difference on Ubuntu. I need to use photoshop, illustrator and other windows based graphics packages but not tried wine as yet.

Thanks,
quilgar

---

### Post by StooJ on 2008-10-09
Yes, grub is looking for the now vanished Ubuntu installation.

Booting into the hardy liveCD will bypass grub, so that's the first step.

Then install Ubuntu, taking care at the partitioning section of the installation. My advice would be to choose "Manual"

Pick the appropriate partitions from the list there and mount them accordingly. Format your 100GB partition and mount it as "/" - it will be in the drop-down box. This will put the entire ubuntu installation in this single partition.

You could also mount your other drives and give them a suitable mount point. Make sure you don't format them though! How about /windows for your windows partition and /mystuff for your 400GB partition. The mount point has a drop down box, but you can type what you like in it as well.

Just as another suggestion, would you be interested in further splitting up your 100GB partition? You've obviously comfortable enough to make partitions yourself, so I'd recommend splitting the 100GB partition into 3 - a 10 to 15GB for the /, 2GB for the swap and the rest (80ish) for your /home

Actually, come to think of it you'll need a swap partition anyway, so you might as well make a home partition too. It means you can reinstall Ubuntu without losing your files & settings

---

### Post by quilgar on 2008-10-09
Hi Stooj,

Many thanks for your response. I will try that when I get home tonight. Did wonder if the solution was so simple as a reinstall but I needed guidance to avoid stuffing myself into a blind-alley and turning my machine into scrap metal. Thanks again.
Quilgar

---

### Post by TeXtonyx on 2008-10-09
[http://www.swerdna.net.au/linhowtoboot1.html](http://www.swerdna.net.au/linhowtoboot1.html)
This explains how to install grub to the root partition of Ubuntu rather than the MBR.
It is written for OpenSuse so just substitute Ubuntu for the OpenSuse references.

If you have to reinstall Ubuntu then do it in the optimum manner for a user who dual 
boots. At step 7, during the live cd install, choose advanced and select the partition to
which Ubuntu is being installed from the drop down windows choices.  The advantage
of this method is that if you lose grub you can still boot your XP drive because the MBR
has been left in tact. If your XP drive doesn't boot now, use fixmbr from the Recovery
Console that is part of the XP install cd. Use Bootpart [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) 
to automatically copy the first 512 bytes of the Ubuntu boot sector,
write it to C:\ and make an entry to boot.ini.
C:\>type boot.ini
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Pro Disk 2" /noexecute=o
ptin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="UbuntuA"
C:\UbuntuB.bin="UbuntuB"

TeX: I have two hard drives with Ubuntu installed to both of them in the boot partition
not the MBR.  I could have made it point to openSuse or another Linux distro, or even
install Vista on the second drive. Since Vista overwrites the MBR,  that means you 
would have to fix it if grub were installed there beforehand.  If the XP drive goes down,
you can still boot Ubuntu with a SuperGrub disk.  On my other computer which has
two drives I triple boot XP, Ubuntu and Vista all from XP's boot.ini; grub's ubuntu.bin
allows me to select the Vista bootloader which is part of menu.lst
For a Ubuntu machine that is only and always going to be purely Linux then grub in
the MBR is fine and I suppose is the reason for the default install to the MBR.  But 
60% of Ubuntu users dual boot. So those users should take advantage of much greater
flexibility of where one can possibly install the Linux grub bootloader while Windows  
doesn't offer that same flexibility. The method I'm advocating let's you troubleshoot 
and fix Windows problems without giving up Ubuntu, troubleshoot and fix Ubuntu 
problems without giving up XP because not all of the eggs are in one basket, so that 
losing a part doesn't cause another part of the whole not to function. 
I do not know of even one practical  reason to install grub to the MBR of a drive which 
is part of a computer system which dual boots with XP. Not one! Perhaps there is an
idealistic Ubuntu reason: Bootpart is free but not Open Source so perhaps Ubuntu 
looks at it in the same way that it does for proprietary (video) drivers which are free. 
code:  sudo fdisk -l    is your friend when it comes to investigating the lay of the land. 

There are two IDE ports on your motherboard where your drive data cables plug into.
The first ide port or primary, lets you connect two ide drives, the master and the slave.
The secondary ide port also lets you connect a master and a slave.
The first drive on the primary IDE port, is the Master and is labeled hd0, while the 
second drive is labeled hd1 (cdrom, dvds usually are attached to the secondary IDE).
gksudo gedit /boot/grub/menu.lst
This lets you add an OS to grub, for instance
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
[makeactive]
savedefault
chainloader	+1
TeX: One can also manually add entries to menu.lst the important part is to get the 
location right of identifying where "  root  " is.  Above the root (hd0,0) says that
XP is installed on the first hard drive (hd0) and in the first partition. That is how
sudo fdisk -l helps, it shows you your partitions and their numbers.  For instance
my Vista drive would be (hd1,0) where hd1 is the second drive. Be aware that 
/dev/sda1 means on the first drive and /dev/sdb1 is on the second drive. I put makeactive
in brackets above because I'm not sure its needed. You can make the title whatever you want.  
Just hd0 without the ,0 partition information means MBR; so does sda. sda1 identifies the first partition.
hd0 is what you change from in step 7 of the live cd install under Advanced.

---

### Post by quilgar on 2008-10-09
Hi Stooj,
Did as per your posting and up and running again. Many thanks.
quilgar

---

### Post by quilgar on 2008-10-09
Hello TeXtonyx,
Thanks for your input. Have followed the link you gave and I am in over my head. As the situation is restored I intend leaving well alone. Have Saved the references though as I intend to keep on a curve with Ubuntu. Thanks for responding.
quilgar

---

### Post by StooJ on 2008-10-09
Glad to be of help.

Could you mark your thread as Solved now, makes it easier for people searching in the future.

Many thanks

---

