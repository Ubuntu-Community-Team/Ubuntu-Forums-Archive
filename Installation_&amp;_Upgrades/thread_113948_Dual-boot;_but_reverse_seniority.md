---
title: "Dual-boot; but reverse seniority"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2006-01-07
Anybody know of a guide for dual-boot when Ubuntu's there first instead of Windows?  Seen several guides assuming that Windows is there already, but none the other way around.

---

### Post by Leif on 2006-01-07
1. create a partition for windows (gparted etc.)
2. install windows
3. boot using the breezy cd
4. mount your ubuntu partition, then run grub-install

should work, but I've never done it personally

---

### Post by ajgreeny on 2006-01-07
Al below assumes you have a floppy drive.
From your current running ubuntu use the terminal to copy your grub to floppy using sudo grub-install fd0.  If you get an error message teling you the floppy is not bios boot listed (or something similar) make sure that the floppy is i9n your /boot/grub/devices.map file.  If not add the line 
(fd0)	/dev/fd0
to the end of the file and then repeat the grub-install fd0

Install windows in the normal way, and then reboot with your newly made floppy in the drive.  This will allow you to start ubuntu.  Now you will need to add windows to your /boot/grub/menu.lst by adding the following to the bottom of the file

# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

You may need to change the partition info for your installation of windows, depending on the disk configuration, but if it is on your only disk then the above should be OK.

Having got this far, you now copy grub back to the hard disk using
sudo grub-install /dev/hda.

All should be OK now!  I hope it all works for you.

---

### Post by Kipper on 2006-01-07
There's one gotcha here, which I don't think has been pointed out. The clue is in the GRUB entry in "menu.lst" for Windows. Notice the "root (hd0,0)". This means Windows expects to boot from the first partition of your disk. So if you have installed Ubunutu here, where exactly can you install Windows? 

Linux on the other hand will boot from any partition. Depending on your current partition scheme, this may mean moving your Ubuntu install to another part of your disk before you can install Windows. It means possibly creating new partition(s) and copying current partitions to a modifeid partition scheme. You will of course have to edit /etc/fstab and menu.lst after this to reflect the changes.

---

### Post by Bartender on 2006-01-08
I only installed Breezy a coupla weeks ago to a blank HDD.  I'm not committed to the current install in any way.  Would it be easier to just install W2K, let it format the entire drive, and then follow some of the guides?  There's more documentation for doing it that way and it might be safer for a Linux newb like me

---

### Post by Kipper on 2006-01-08
To be honest, I think on balance it might be easier for you to reformat your disk and start from scratch.

Install W2K first but DO NOT let to it use the entire disk, leave enough free space for your Linux install which will save messing around with resizing the Windows partition(s). If your are going to format it for NTFS. I would also recommend creating a FAT32 partition which can you both read and write to from either Windows or Linux. 

As you say, there are plenty of guides around for installing Ubuntu after Windows which will leave you with a dual-boot system. Good luck with it...

---

