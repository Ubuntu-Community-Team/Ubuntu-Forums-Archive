---
title: "Grub 1.5 Error 17"
date: 2008-09-19
forum: General Help
---

### Post by ZybezJessica on 2008-09-19
When I boot up - I get error 17.


Step by step guide of what I did:



Format my Ubuntu Partition (dual booting XP - Two hard drives)

Create a new partition where the old ubuntu one was.


Now I get error 17 and my computer is un-usable.

(I was trying to uninstall Ubuntu)

Any help is much appreciated.


NO - I DON'T HAVE AN XP DISK.

---

### Post by stickmangumby on 2008-09-19
Grub has an error because the partitions that it knows about don't match the actual partitions on the harddrive.

If you did have a windows XP CD (or can borrow one), you could boot into the command line and run "fixmbr"

You can also boot to a bootable DOS CD and do the same thing.

Alternatively, you can boot up your Ubuntu live CD and run "sudo grub-install" from the terminal. I think that's right anyway.

---

### Post by ethan_p on 2008-09-19
> **ZybezJessica said:**
> When I boot up - I get error 17.
NO - I DON'T HAVE AN XP DISK.

Well it sure would help, because booting it into the recovery console and running fixmbr is the easiest way to fix it.

If you still have a linux install (you didn't specify - it looks like you only have two windows installs from my pov) then you could grub-install.

Otherwise, you can try the hard way: boot into a linux liveCD and write the first 446 bytes of the MBR with zeroes:

dd if=/dev/zero of=/dev/sda bs=446 count=1

**Do not write to any bytes after that unless you want to overwrite your partition table.**

Use fdisk and make sure one of the windows partitions has the bootable (active) flag set. When you boot, the BIOS will see that there's nothing in the MBR, find the first partition with the bootable flag set and jump into the VBR of that partition and all should be fine. You should boot into that Windows install.

*note: this is not guaranteed, some BIOSes don't support this*

If it doesn't work - well, you're in no more trouble than you were before that.

---

### Post by ZybezJessica on 2008-09-20
As a temp. Solution can I just re-install Linux from the Live CD?

---

### Post by Sef on 2008-09-20
> As a temp. Solution can I just re-install Linux from the Live CD?


If that works that would be a permanent solution.  **Back up** everything if you do.

---

### Post by ZybezJessica on 2008-09-20
Another tech forum suggested I use SuperGrubDisk - just confirming - is this reccomended?

---

### Post by stickmangumby on 2008-09-20
The SuperGrubDisk will work as well. It will allow you to fix up the error that Grub is having, and then you can boot into Windows and do a "fixmbr" from the command prompt and you'll be fully Windows-ed again.

---

### Post by TeXtonyx on 2008-09-20
[http://forjamari.linex.org/frs/?group_id=61&release_id=645#645](http://forjamari.linex.org/frs/?group_id=61&release_id=645#645)
Under USB download and then extract; you need the grub directory.
super_grub_disk_english_usb_0.9755.tar.gz
-----------------

[http://www.7-zip.org/](http://www.7-zip.org/)
Free tool to extract tar.gz files.

---------------------

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Re-install GRUB with a GRUB shell
The first step is to open a terminal and open a grub shell with root priveleges,
Code:
$ sudo grub
Type "sudo grub" (without quotes) and press "Enter".

This creates a GRUB shell, it has a GRUB prompt, like this, 'grub>_'    

grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Here, I typed 'find /boot/grub/stage1'. That's a test to find out or confirm 
which partitions in my computer have GRUB installed in them.
This gives me a clue as to exactly where the necessary GRUB files may be 
located that I can install GRUB *from*.

[That is an example. Most likely your /boot/grub will be on sda1 (XP)
so the find command will more likely report something like (hd0,0<-?) 
because that is where you extracted it with 7-zip. ? will be a number]

type   grub> root (hd0,1) <enter>

The 'root (hd0,1) will tell GRUB which operating system partition contains 
the GRUB I want to install from.  It has to be one of the ones listed by 
the 'find' command (above). [in your case, perhaps (hd0,0)]

type   setup (hd0,1) <enter> 
To install GRUB to a partition, you would use a command like, 'setup (hd0,1)
The 'setup' command is the command that tells GRUB exactly where to install 
Grub to. [I assume Ubuntu is on the second partition of the XP drive. If you 
have a Fat32 partition in between them it changes the numbering. You can 
check by typing the command, sudo fdisk -l, which will report the ordering.]
------------------------

[http://aumha.net/viewtopic.php?f=62&t=31844](http://aumha.net/viewtopic.php?f=62&t=31844)
Installs Recovery Console on your hard disk. For future reference.
------------------------------

This is what my boot.ini looks like after all of the steps.

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\ubuntu.bin="Ubuntu"

ubuntu.bin is the first 512 bytes of the Ubuntu boot partition which I think
will be on the second partion of your hard drive, after the XP installation.
In order to use this method, grub is installed to first sector of the Ubuntu
boot partition, which is what those grub commands accomplished.
----------------------------------

The easiest way to capture those 512 bytes is to use Bootpart from XP. After 
Bootpart creates ubuntu.bin, it also adds C:\ubuntu.bin="Ubuntu" to boot.ini
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)  	 bootpa26.zip Bootpart 2.60 in English.
--------------------------

Grub is installed by default to the MBR, which is only place if one just
has Ubuntu installed. But it is not the best default for dual boots. The
first sector, 512 bytes, of the Ubuntu boot partition is the best place.
The steps above may be too complicated for you. The best time to install
grub to the first sector of the Ubuntu boot partition is during the initial
installation: after making your partition choices, there is a screen which
comes up that has an "Advanced" option and this gives you a chance to
install grub to the Ubuntu boot partion, not the MBR. Usually sda1. 

The advantage of this is easier troubleshooting and repair, if you decide
to uninstall Ubuntu one doesn't need to fixmbr with Recovery Console. And
if Windows breaks, a Super Grub disk can boot Ubuntu from its partition.

If you have a floppy drive and Mtools package installed you can download
a win98se(oem) boot (floppy) disk and use the command fdisk /mbr
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

---

