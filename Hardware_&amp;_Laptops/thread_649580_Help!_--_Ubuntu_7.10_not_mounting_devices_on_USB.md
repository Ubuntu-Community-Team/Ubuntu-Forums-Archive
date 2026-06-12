---
title: "Help! -- Ubuntu 7.10 not mounting devices on USB"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by todd1049 on 2007-12-25
I just upgraded to Ubuntu 7.10 from 7.04 and am now unable to mount USb data devices like my external hard disk or a thumb drive.  However, strangely, the system recognized my camera when I plugged that in.  trying sudo mount gives me a message that /media/usb does not exist, and the dmesg command gives me the following message

[  294.104000] sdd: Mode Sense: 27 00 00 00
[  294.104000] sdd: assuming drive cache: write through
[  294.104000] SCSI device sdd: 312581808 512-byte hdwr sectors (160042 MB)
[  294.104000] sdd: Write Protect is off
[  294.104000] sdd: Mode Sense: 27 00 00 00
[  294.104000] sdd: assuming drive cache: write through
[  294.104000]  sdd: sdd1
[  294.152000] sd 5:0:0:0: Attached scsi disk sdd
[  294.152000] sd 5:0:0:0: Attached scsi generic sg4 type 0
[  294.492000] FAT: Unrecognized mount option "usefree" or missing value

Can anyone suggest how I might fix this?  Many thanks for the help.

---

### Post by karthikp on 2007-12-25
I can confirm this partially on Kubuntu. All known* devices mount as normal when plugged in. But devices that are already attached at boot up time do not automount.

*known = devices that I set the preferences for. Plug them in. Look in konqueror in the media:/ ioslave and specify such things as the mount point and the permissions (using a terminal, sudo chmod a+rwx)

---

### Post by todd1049 on 2007-12-25
Karthikp, I had the problem you describe intermittently with v7.04 of Ubuntu as well -- devices that were already plugged in to the USB drive on boot-up at time were at times simply ignored by the system.  But in this case, with v7.10, the problem I am having is that the system is explicitly telling me that it can not mount devices I am plugging in after boot-up.  Again, any suggestions anyone can offer would be greatly appreciated.

---

