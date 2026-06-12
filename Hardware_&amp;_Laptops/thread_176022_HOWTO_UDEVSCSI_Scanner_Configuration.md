---
title: "HOWTO: UDEV/SCSI Scanner Configuration"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by TWFJR on 2006-05-14
January 18th, 2005, Gordo responded to UDEV SCSI Scanner Configuration.  Where, the command:  sudo gedit /etc/udev/udev.rules results in output of:  # permissions for SCSI sg devices
BUS="scsi", KERNEL="s[grt][0-9]*", SYSFS_type="5", NAME="%k", MODE="0660", GROUP="cdrom" as demonstrated but, the command fails to give this line on my computer.  Instead, no line begins with the word permissions for SCSI sg devices. What does exist is a line SCSI devices BUS="scsi", KERNEL= "sr[0-9]*", NAME= "scd%on", SYMLINK+= "sr%on".  I added the lines you instructed to add, substituting the exact model name of your scanner.  I'm assuming that, " user is a member of the scanner group."  If not, then how does one verify that one's user name is of the scanner group?  Is there a problem with no permissions line as indicated in /etc/udev/udev.rules?

---

