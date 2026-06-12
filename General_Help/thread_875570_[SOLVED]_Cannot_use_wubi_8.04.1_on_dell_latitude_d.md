---
title: "[SOLVED] Cannot use wubi 8.04.1 on dell latitude d820 with vista"
date: 2008-07-31
forum: General Help
---

### Post by cypherstream on 2008-07-31
Hello,

I'm having a heck of a time getting Ubuntu to run on a dell latitude d820.  I don't want to mess with the drive partitioning so I want to play with it using wubi.  The laptop came with Vista Ultimate on it, and there's two partitions it seems like.  The C:\ drive and an S:\ drive with a few hidden files.  This might be a dell diagnostic tools that I can't remove.

The first problem is that when selecting Ubuntu in the windows boot loader, I would have an error message stating that GLDR or something isn't found.  So next I copied a few wubi files (I think there were 3 or 4) including the menu.lst file from the C:\ drive to the S:\ drive.  Now when I boot it flashes something really fast like Entering cmain(), something about memory E820, something about A20, etc..  So figuring it was a Gate A20 issue I downloaded wubildr.zip from another thread on this very forum.  Now I am able to do a line by line check by pushing insert.  Here's where I'm at now:

> Get upper memory
hard drives: 1, int13: F0007C21, int15: F000F859
get_diskinfo(80), int13/41(80),version=AA210005,  int13/48(80),err=0, C/H/S=16383/16/63, Sector Count/Size=312581808/0,  int13/08(80),version=0, C/H/S=1024/255/63,  int13/02(80),err=0,
Warning: MBR cylinders(19458) is not equal to the BIOS one (16383)

Warning: MBR total sectors(312592770) is greater than the BIOS one(312581808).
Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.  LBA, C/H/S=19458/255/63, Sector Count/Size=312592770/512

boot drive=80,  int13/4B01(80),err=1,drive=80, Not CD

get_cdinfo(7F), int13/4B01(7F),err=1,drive=7F, cdrom_drive == FFFFFFFF.

Starting cmain() ... Open (128,2)/default ... failure.


End of menu init commands. Press any key to enter command-line or run menu...


Pushing any key then proceeds to flash text really quickly in the upper right corner of the screen.  Looks like these phrases are repeating forever:
Starting cmain()...
Something about "Memory" (too fast to see)
Something about "A20" (way too fast to see)

Any idea's what I could do?  I went to this site: [http://wubi-installer.org/](http://wubi-installer.org/)  and downloaded the latest wubi.  It downloaded the ubuntu 8.04.01 install.  It took about a little over an hour to install.

Is it a problem with the Dell Latitude D820 laptop?  I updated the bios from version A06 to A09 and it didn't fix the problem.

Is it a limitation with Windows Vista?

Thanks for your help!

---

### Post by tinybit on 2008-07-31
If you would like, please take a try with this grub4dos(the latest build):

[http://nufans.net/grub4dos/grub4dos-0.4.4-2008-07-28.zip](http://nufans.net/grub4dos/grub4dos-0.4.4-2008-07-28.zip)

Grub4Dos tutorials can be gained here:

[http://grub4dos.sourceforge.net/wiki](http://grub4dos.sourceforge.net/wiki)
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

or here:

[http://diddy.boot-land.net/grub4dos/Grub4dos.htm](http://diddy.boot-land.net/grub4dos/Grub4dos.htm)

And Grub4Dos support forum(in English) is here:

[http://www.boot-land.net/forums/?showforum=66](http://www.boot-land.net/forums/?showforum=66)

---

### Post by cypherstream on 2008-07-31
Well I copied vmlinuz from the C:\ drive to the S:\ drive and now when I choose ubuntu in the Windows boot menu, it shows the Ubuntu logo for a little bit and then puts me at a busy box prompt (initramfs)

Here's the output of cat /proc/mounts
rootfs /rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0

Here's the output of cat /proc/partitions:
major  minor  #blocks   name
8       0     156290904  sda
8       1     72261      sda1
8       2     154680320  sda2
8       3       153600   sda3

Output from grep err /casper.log
Could not find the ISO /ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso. This could happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows. After this you should be able to reboot again and resume the installation.

Output from grep mount /casper.log
Could not find the ISO /ubuntu/install/ubuntu-8.04.1-desktop.amd64.iso  This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, or an improper shutdown, or unplugging of a removeable device without first unmounting or ejecting it.  To fix this, simply reboot into Windows let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows. After this you should be able to reboot again and resume the installation.

I think what's happening here is that it's looking for the iso on the S:\ drive for whatever reason.  There's no way I can move the stuff form the C:\ to the S:\ drive, because the S:\ partition is only 1GB, and I reserved 30GB on drive C:\ for the installation.  Why won't it see the C:\ drive?  Am I onto something here?  I can't tell you why there's a 1GB S:\ drive.  All I can figure is that Dell put it there from the factory.  This is my work's laptop, but I work in IT, so I have complete control over it if you think running something like partition magic to mess with the disk would fix it.

I read on slashdot yesterday something about Vista SP1 refuses to install in a dual boot configuration because SP1 thinks the bootloader has been tampered with.  Well I already have SP1 on, so this isn't going to break anything in the long term is it?

Thanks for your help.

---

### Post by ago on 2008-08-01
If you installed on C: there should be no need to move files around. It should be able to find them in C: unless the drive is not supported by grub for whatever reason

---

### Post by cypherstream on 2008-08-01
Well yes, I did select to install on C:\ drive, and that's where the files were originally.

If I don't copy those few files to the S:\ partition I get this when I try to boot Ubuntu:


Try (hd0,0): FAT16: No WUBILDR
Try (hd0,1): NTFS5: 2
Try (hd0,2): NTFS5: No wubildr
Try (hd0,3): invalid or null
Error: Cannot find GRLDR in all devices.  Press Ctrl+Alt+Del to restart.


So what now?

---

### Post by ago on 2008-08-01
hd0,1 (=sda2) is where it should be given your post above

Not sure with the #2 code means in grub4dos will ask tinybit/bean123

Try (hd0,1): NTFS5: 2

---

### Post by cypherstream on 2008-08-01
Ok I think I found the problem.  This Latitude D820 with Vista Ultimate was given to me with that "BitLocker" drive encryption turned on.  I did some research and figured out how to get rid of it.  It took awhile but there was a control panel applet to decrypt the drive.  Then I had to make the C:\ partition active in the disk management snap in.  Next I had to reboot and use the Windows Vista installation CD to repair the boot sector.  Finally one more reboot with the install CD to repair the boot files to the C:\ partition.  Then when back in Vista I was able to delete the S:\ partition and extend C:\ to fill the drive. 

I'm now doing a full download install and we'll see how it goes.  I'm pretty confident that the problem should be resolved as the BitLocker is heavily encrypted with the TPM chip, hence wubi could not read the C:\ partition.  The S:\ partition is a side effect of having a "BitLocker" encrypted drive.  The system boots from an S:(System) partition which is 1.5GB in size and does all the decryption stuff there.

---

### Post by cypherstream on 2008-08-01
Yup it works now!!!

---

