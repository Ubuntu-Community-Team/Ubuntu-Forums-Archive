---
title: "Is my HDD really dead?"
date: 2012-10-14
forum: Hardware
---

### Post by jeffpkamp on 2012-10-14
I had a windows 7 computer that stopped working suddenly and gave me a Disk Read error message.  I could not access the HDD in the windows recovery environment so I attached it to my computer I have Ubuntu installed on.  I cannot boot up Ubuntu with the drive attached to the SATA port.  However, I got it started with the drive disconnected from the computer, and then hooked it up with a USB external case.  Gparted and Disk Utility recognize the drive and show the partitions correctly.  However, the partitions are listed as "Unrecognize" and there is no option to mount the volumes/drive or check the file system. SMART is not available (I’m assuming this is because it is attached through the USB).  Attempts to use the format, benchmark, etc... buttons leads to errors about read write (as below):

Error creating file system: helper exited with exit code 1: helper failed with:
Error writing to /dev/sdb2: Input/output error
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/output error
Failed to fsync device /dev/sdb2: Input/output error
Warning: Could not close /dev/sdb2: Input/output error

Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.

I am trying to decide if my HDD is cooked, or if there is some program or terminal programs that I could use to get at my old files, or just format the drive so I can use it again.  Any help is appreciated

---

### Post by ahallubuntu on 2012-10-14
Well, you need to check S.M.A.R.T. somehow.  Yes, often USB bridges aren't automatically detected by the S.M.A.R.T. tools.  I recommend you install GSmartControl in Ubuntu and try viewing the S.M.A.R.T. Attributes again.  If you still can't read the data, try adding arguments to the smartctl command (which you could also run directly in a terminal).

Here's some info on that:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

but generally, try adding -d sat and/or -T permissive to the command.

Also, if you want to try the SATA connection again, check the order of the SATA connectors on your motherboard.  If the Ubuntu drive isn't now plugged into the FIRST SATA port, change it to the first one and plug your failing drive into another port and see if it will boot that way.

---

### Post by jeffpkamp on 2012-10-15
Alright, so I had already tried both of these options with the programs freezing or giving me error messages when I tried accessing the drive.  But it seems my drive appreciated me not prodding it all night.  I can see the smart data with GSmartControl, and its not good, with 4 attributes listed as pre-fail, having to do with writing bad sectors.  The last three error codes are:  

Error: UNC 8 sectors at LBA = 0x002ee800 = 3074048

I tried running the short test, but it said "completed with read failure".   I tried running it again and it informed me the drive was not detected.  I told GSC to rescan for the drive, it found it, then I told it to run the short test again.  It started and said it was starting smartctl, then froze.  When I clicked cancel after 10 min, it said aborting, then froze...  not sure what to do.  All this is making me think that my drive has some serious physical issues.  Any advice?

---

### Post by jeffpkamp on 2012-10-15
I've attached the SMART data, since it will probably help understand whats happening.

---

### Post by ahallubuntu on 2012-10-15
Yes, 265 sectors have already failed and been marked so by the drive firmware as "reallocated" (replaced by spares), and 41 sectors are still pending (can't be read).  Yes, the drive is toast.  Happens all the time.  Hard drives fail routinely.

---

### Post by jeffpkamp on 2012-10-16
okay, that's what I figured, thanks for the help.  Is this something that I might have a chance of recovering some files with using ddrescue?  Or any other data recovery suggestions would be appreciated.

---

