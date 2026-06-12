---
title: "How to check if hard disk is faulty?"
date: 2011-12-19
forum: Hardware
---

### Post by mastablasta on 2011-12-19
Do i use testdisk to do it?
 
I was really stumped over the weekend as after repeated windows XP installs i couldn't reboot the os propperly. so i tried linux. Lubuntu first. during Live boot it immediatelly did a disk repair. after that i rebooted, no boot again.
 
Then i tried to go Kubuntu as it has a bit more apps on live disk, loaded up the usb, grub started i chose try without install. then i went away when i come back instaed of Kubuntu windowsXP loads perfectly. i am really stumped. I've been at this Caviar gfreen disk for some time now. and now i am considering it might be a faulty disk. but is there a way to check that in linux? Disk is NTFS formated with partitions already aligned.

---

### Post by Paddy Landau on 2011-12-19
Boot into Ubuntu (a Live CD is fine), and open Disk Utility.

On the left-hand side, click on your suspect drive.

If the drive has SMART data, you will see a couple of items on the right-hand side indicating whether or not the disk state is healthy, and an option called SMARTdata. Try the SMARTdata; read what it says and, if necessary, Run Self-Test.

If you suspect that your drive is failing, I would recommend first trying to back up all your data first, as highest priority. You can probably do that from your Live CD, if your data is still accessible.

---

### Post by mastablasta on 2011-12-20
> **Paddy Landau said:**
> Boot into Ubuntu (a Live CD is fine), and open Disk Utility.
 
On the left-hand side, click on your suspect drive.
 
If the drive has SMART data, you will see a couple of items on the right-hand side indicating whether or not the disk state is healthy, and an option called SMARTdata. Try the SMARTdata; read what it says and, if necessary, Run Self-Test.

 
Thanks. Will have a look. 
 
SMART is disabled (says so on boot). should i enable it? 
 
> 
If you suspect that your drive is failing, I would recommend first trying to back up all your data first, as highest priority. You can probably do that from your Live CD, if your data is still accessible.
 
It's a brand new drive with only windowsXP freshly installed. that's why it's puzzling. WD says it might be faulty. We will try to run their diagnostic utility and change the SATA cable in case the cable is faulty.
Funny though it stopped booting again, but once Kubuntu was booted from LiveUSB (seems it must have repaired the disk again) it booted well to the WinXP. I guess it happened same as with lubuntu it saw a faulty disk/file system and decided to repair it before booting up.

---

### Post by Paddy Landau on 2011-12-20
> **mastablasta said:**
> SMART is disabled (says so on boot). should i enable it?
Sorry, I don't know enough about SMART.
 
> **mastablasta said:**
> It's a brand new drive... Funny though it stopped booting again, but once Kubuntu was booted from LiveUSB (seems it must have repaired the disk again) it booted well to the WinXP. I guess it happened same as with lubuntu it saw a faulty disk/file system and decided to repair it before booting up.
I suppose that is possible, though why Windows should cause problems, I don't know.

What about deleting all partitions and then reinstalling Windows from scratch? At a guess -- but just a guess -- there may be something wrong with the partitions or the drive's formatting. Windows XP "should" create the partitions and reformat on installation.

---

### Post by mastablasta on 2011-12-21
already tried that. reformat, quick format & reinstall, reinstall only (overwrite), partition alignment. cloning partition using clonezilla & redobackup... unless stuff improved by switching the SATA cable then disk is faulty.
 
funny though that chkdk doesn't find any errors, while linux repairs file system error. :-)

---

### Post by Paddy Landau on 2011-12-21
I wonder if you can use a tool to check all the sectors on the disk? Doesn't Windows's chkdsk have an option to do that?

---

### Post by crazy bird on 2011-12-21
[http://packages.ubuntu.com/lucid/utils/smartmontools](http://packages.ubuntu.com/lucid/utils/smartmontools)

---

### Post by mastablasta on 2011-12-22
> **Paddy Landau said:**
> I wonder if you can use a tool to check all the sectors on the disk? Doesn't Windows's chkdsk have an option to do that?
 
yup. checkdisk didn't find any errors. ran the WD disk utility - no errors. low level format (zeroes) new partitions. new SATA cable. same issues.
 
it seems disk is ok. 
 
i believe the errors are made when shutting down the OS (windows) that data don't get written propperly to disk. because as long as you leave it running it all works ok. 
 
so i narrowed it all down to:
- drivers (perhaps there is a need for special drivers)
- BIOS - oldish bios, maybe it doesn't support these green disks?
- failing motherboard
- failing PSU
 
i think it must be a hardware issue on another component.

---

### Post by Paddy Landau on 2011-12-22
Hmm, I suspect you are right about the drivers. I would not suspect the hardware for the simple reason that Linux doesn't have the problem and indeed solves it.

I don't remember how to get Windows to search for drivers, but perhaps that is the way forward?

---

