---
title: "mounting HD using live CD"
date: 2010-11-11
forum: Hardware
---

### Post by iamgoodattehinternet on 2010-11-11
Total noob here. Recently my OS crashed (ubuntu 10.10) and I am trying to get the files off of my HD with a live CD. It was improperly shut down, so i'll need to force mount it (unless someone knows how i can properly reboot using busybox?). 
When i attempt a force mount i get the message:
"NTSF signature is missing. Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instad of partition (e.g. /dev/sda. not /dev/sda1)? or the other way around?"
I've tried "sudo apt-get install ntsf-config" and get E: Unable to locate packagers ntsf-config.

---

### Post by linux-hack on 2010-11-11
try making a **fsck** on you hd ... and you have the force option from the mount command ...

---

### Post by CharlesA on 2010-11-11
If you are having a problem with an NTFS partition, the best thing to do would be to hook it up to a Windows box so that you can run chkdisk on it.

---

### Post by iamgoodattehinternet on 2010-11-11
Is there a command in terminal to "fchk"?
in trying to use disk utility i get the response "an error occurred while performing an operation on "154 GB filesystem"(partition 1 of ATA WDC WD1600BEVS-60RST0): The device is busy"
Unfortunately, i do not have a windows box to put it in.

---

### Post by wilee-nilee on 2010-11-11
> **CharlesA said:**
> If you are having a problem with an NTFS partition, the best thing to do would be to hook it up to a Windows box so that you can run chkdisk on it.

+1 OP I would do this.

---

