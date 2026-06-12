---
title: "floppy not dectected"
date: 2010-11-26
forum: Hardware
---

### Post by whvw on 2010-11-26
No matter what I do, my Ubuntu 9.10 will not recognise floppies. It shows the drive as present, but I always get an "unable to mount location, no media in drive" message. "Disk Utility" and "Mount Manager" have been of little help.

---

### Post by chideock on 2010-11-27
I am running 10.04 Desktop and have the same issue. Shows the Floppy but when selected the error "Unable to mount location" "No media in the drive" when there is media in the drive. "Sudo modprobe floppy" returns nothing. My fstab has the device line - /dev/fd0   /media/floppy0 auto  rw,noauto,user, sync  0 0.
System-Admin-Disk Utility shows the floppy as /dev/fd0 but "No Media Detected" when there is media.

I wanted to make a "smart boot manager" floppy but can not under these circumstances.

Any thoughts?

I did google this issue and got old bug reports that are marked solved and did try other suggestions including adding "floppy" to modules returns error "An error occurred while mounting /media/floppy0" on startup.

---

### Post by chideock on 2010-11-27
In the instance:
/etc/modules edited so that the module "floppy" is NOT specified in that file
/etc/fstab has the line  - /dev/fd0   /media/floppy0 auto  rw,auto,user, sync  0 0.
no media in the floppy on start
On start up the error  "An error occurred while mounting /media/floppy0"occurs
Pressing "S" to start Ubuntu then "sudo modprobe floppy" gives nothing
Inserted media is not detected

If media is in the floppy then no error occurs Ubuntu starts but 
 then "sudo modprobe floppy" gives nothing
Inserted media is not detected

In the instance
/etc/modules edited so that the module "floppy" IS specified in that file
/etc/fstab has the line  - /dev/fd0   /media/floppy0 auto  rw,auto,user, sync  0 0.
no media in the floppy on start
On start up the error  "An error occurred while mounting /media/floppy0"occurs
Pressing "S" to start Ubuntu then "sudo modprobe floppy" gives nothing
Inserted media is not detected

If media is in the floppy then no error occurs Ubuntu starts but 
then "sudo modprobe floppy" gives nothing
 Inserted media is not detected

---

### Post by coffeecat on 2010-11-27
With a floppy in the drive, try this from the terminal:

```
udisks --mount /dev/fd0
```

---

### Post by chideock on 2010-11-27
Going back to "noauto" in fstab obviously eliminates the errors on startup.

Very good - using sudo udisks --mount /dev/fd0 -- works

One can copy files from the floppy with this but can not copy files to the floppy.

---

### Post by chideock on 2010-11-27
Well -- experimenting some more and I found that I could write to the floppy. I wanted this to make a Smart Boot Floppy. So I used the command in terminal as per Ubuntu docs and found that worked with the floppy mounted by udisks.

I guess udisks only works for terminal write commands and not write commands in GUI. Although in GUI one can copy files from the floppy.

---

### Post by coffeecat on 2010-11-27
> **chideock said:**
> One can copy files from the floppy with this but can not copy files to the floppy.

I can write to floppy with this. The actual write is not committed until you unmount the drive by right-clicking on the desktop icon. Also - make sure you don't have the write protect tag in the read-only position.

**EDIT:** You posted as i posted.

> **chideock said:**
> I guess udisks only works for terminal commands and not GUI.

Not so. I can write with drag and drop in the GUI after mounting with the udisks command.

---

### Post by chideock on 2010-11-27
OK now that you have said that I will try again with gui

Get "permissions denied" in gui and terminal

OK did udisks to mount the floppy -- then did sudo nautilus to open a window with root privileges then I was able to move files using the / file browser and a places files browser

Thanks coffeecat

---

