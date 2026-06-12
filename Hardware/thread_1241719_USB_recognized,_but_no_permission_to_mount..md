---
title: "USB recognized, but no permission to mount."
date: 2009-08-16
forum: Hardware
---

### Post by cscomp3 on 2009-08-16
When I first installed ubuntu, 8.10, usb drives mounted fine. Then somewhere along the way, I lost permission to mount them. I upgraded to Jaunty, hoping to fix the problem, but I still don't have permission to mount the usb drive. The system "sees" it under PLACES -> COMPUTER as "4.1 GB Media", but when I plug it in, I get a dialogue box stating "Cannot mount volume. You are not privileged to mount this volume." I get the same dialogue box when I right click and try to mount it from the drop down menu. My username is an administrator and the "Access external storage devices automatically" box is checked under SYSTEM -> ADMINISTRATION -> USERS & GROUPS.   Help!  I need to do some backups!

---

### Post by nixscripter on 2009-08-16
Are you a member of the "plugdev" group that HAL uses? Type **groups** into a terminal and make sure it appears.

---

### Post by cscomp3 on 2009-08-18
I am a member of **plugdev**.  It shows when I type **grou**p in a terminal.  However, it does not show in the gui for managing users.  Not sure about that one unless it just follows the check box for permssions.
 
This one is solved. I ran **dmesg** and found where the system was trying to mount the usb drive. It was trying to mount the usb drive to the same locaiton as an old hard drive that was no longer in the system. I ran **sudo gedit** and took the appropriate line out of **fstab.** The usb drive mounts just fine now.

How do I mark this as solved?

---

### Post by nixscripter on 2009-08-19
It's "Mark as Solved" (under the Thread Tools Menu).

---

### Post by jheis on 2009-08-21
Since the OP solved his problem, I thought I'd hijack his thread because I'm having exactly the same problem.  Jaunty initially mounted the hard drive automatically, but now says "Unable to mount location""Can't mount file." 

The output from dmesg is below:

[ 1596.592091] usb 1-4: new high speed USB device using ehci_hcd and address 5
[ 1596.762714] usb 1-4: configuration #1 chosen from 1 choice
[ 1596.803968] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1596.806306] usb-storage: device found at 5
[ 1596.806311] usb-storage: waiting for device to settle before scanning
[ 1601.804280] usb-storage: device scan complete
[ 1601.833398] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1602.595521] sd 3:0:0:0: [sdb] 7839744 512-byte hardware sectors: (4.01 GB/3.73 GiB)
[ 1602.595999] sd 3:0:0:0: [sdb] Write Protect is off
[ 1602.596024] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1602.596030] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1602.600891] sd 3:0:0:0: [sdb] 7839744 512-byte hardware sectors: (4.01 GB/3.73 GiB)
[ 1602.601374] sd 3:0:0:0: [sdb] Write Protect is off
[ 1602.601380] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1602.601385] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1602.601393]  sdb: sdb1
[ 1602.625105] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1602.625232] sd 3:0:0:0: Attached scsi generic sg2 type 0

Oh, by the way, the drive mounts just fine on another laptop running RHEL4.

I'm a newbie at this, so if anyone can tell me what I'm doing wrong I'd appreciate it.  TIA

James

---

### Post by randomjoh on 2011-09-13
Relative issue on 11.04:
fstab no longer shows ntfs vfat32 drives.
Usbs will no longer mount.
Disk Management gives message: "There are no filesystems which you are allowed to mount or unmount. Contact your administrator."
I am a member of the plugdev group.
Any suggestions? :confused:

---

### Post by coffeecat on 2011-09-13
@randomjoh, please do not necromance old, stale threads. You have already started a thread which seems to be the same problem, here:

[http://ubuntuforums.org/showthread.php?t=1843153](http://ubuntuforums.org/showthread.php?t=1843153)

Please continue on in that thread. I'll bump it for you by posting a question.

---

