---
title: "I updated and now can't boot!"
date: 2008-09-11
forum: General Help
---

### Post by quaders on 2008-09-11
Hi,

 I just did some updates on Hardy Heron and it came up with a message saying I could only do a partial update, I did this and now I cannot boot in Ubuntu.  I can start Grub and select to boot into Ubuntu (I am dual booting with Windows XP) but it hangs up on the loading page with the logo on it.  I booted in recovery mode and it hung on that too.  The last couple of lines were:

Begin: Mounting root file system... Begin: Running /scripts/local-top... done.
Begin: Waiting for the root file system... _

And will not go beyond this point.  It lloks pretty bad to me but I don't really know where to start, am I able to use the CD to fix the problem or do I have to reinstall?  I don't know if it has any relevance to it but the last thing I did before the update was to install nmap and zenmap onto the system although i have not done anything with them yet.

Any help would be greatly appreciated!!

---

### Post by Titan8990 on 2008-09-11
I have this problem when I don't shut down Windows properly and it doesn't unmount the drives. Try booting into to Windows, do a graceful shutdown and then try to boot Ubuntu.

---

### Post by cdtech on 2008-09-11
Do you have a second or backup kernel to boot into from the GRUB menu list?
I would select a previous kernel to boot into if you can. If not then you'll need to boot into your Live CD to troubleshoot the problem.

---

### Post by quaders on 2008-09-11
Hi,

I tried the above, the problem occured after running Ubuntu, I had not been into XP recently. I have been back into XP and logged out correctly but this has made no diffrence.  I don't have an older kernal available on the grub menu so I am going to have to boot using the live cd.  I believe the problem is going to be with the software which has been messed up by the partial restore, could anyone give me a couple of pointers as to what to look for or to try when using the live distro to recover Ubuntu.  Are there any commands I can type in order to try and narrow down where the problem lies.

Sorry, I am very new to linux and therefore any help is very much appreciated.

thanks

---

### Post by quaders on 2008-09-12
I tried waiting with it looking for the root device and after several minutes it came up with a warning and dropped into the shell.  The message was:
-Alert! /dev/disk/by-uuid/d6117820-1178-47aa-9533-9eabab3a4a9e does not exist. Dropping to shell.
(initramfs)_

I had a look at the uuid for my hdd containing linux (hd1,0) and it appears to be the correct drive uuid (i looked in /dev/disks/by-uuid/ i'm assuming this would be the correct uuid as it won't complete the vol_id command)

I have noticed in my wanderings that the hard drives are referred to hda1, hd1,0 and sdb1 in diffrent places, i was wondering if sdb1 refers to sata hard drives which i do not have, just a thought you might be able to clear up for me.

---

### Post by cdtech on 2008-09-12
If you could boot into the Live CD open a terminal and type "sudo fdisk -l" to see the proper drive array. You may need to edit your "/boot/grub/menu.lst" to reflect the proper "root /dev". The "menu.lst" uses the GRUB drive scheme such as (hd0), (hd1) I have a list below to show the comparisons.
```
title		8.04.1, kernel 2.6.24-17-generic
**root		(hd0,0)**
kernel		/vmlinuz-2.6.24-17-generic **root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1** ro quiet vga=792
initrd		/initrd.img-2.6.24-17-generic
quiet
```
You can just replace the UUID in the menu list with the /dev/sd?
This: root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1
Would be: root=/dev/sd?

**Examples of the difference from the GNU/Linux and GRUB device names:**

**1st Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

**2nd Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

---

### Post by quaders on 2008-09-12
Hi,

I tried what you suggested, the terminal output for the fdisk command was that linux was on /dev/sdb1 I changed this in the menu.lst and it still fails at the same point on the boot sequence.  I also changed it to hdb1 and tried that as i remember reading somewhere that this is for ide hard drives as i do not have sata drives, this had the same effect.

my menu.lst is now very similar in appearance to your example, i was wondering if it would have messed up my system as i have recently (about half a day before the problem) install a western digital my book 1TB usb2 drive on my system?

My thanks for your continued assistance.

---

