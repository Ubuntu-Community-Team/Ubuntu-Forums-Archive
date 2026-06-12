---
title: "loost connection to external usb3 NTFS-formatted hard disk"
date: 2018-05-19
forum: Hardware
---

### Post by dieter-erich on 2018-05-19
Hi,
   my NTFS-formatted USB3 hard disks mounted on my ubuntu-14.04 box usually run without problems. However, I recently lost connection to all of them; despite them physically still being connected, none of the commands 'blkid', "df", "lsusb", "gparted" finds them. Last time when this happened I could only get them connected by unplugging / reboot / replugging. This time I am not at the site and need a solution from remote! I do not want to reboot from remote because one of the internal disks does not mount automatically and requires a console input - (namely the answer 'Y' to 'skip trying to mount' that I cannot enter at boot time). Is there a way to power-cycle them via a command? Or, even better, how can I solve this problem permanentely? Any ideas welcome!
Thanks, D-E

---

### Post by dieter-erich on 2018-05-19
For those interested: I finally found the solution: [https://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line](https://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line)
Answer <46> worked perfectly for me! I run the script and all USB HDs mounted automatically!

---

### Post by TheFu on 2018-05-19
If you've solved this, please mark the thread as solved to help the rest of the communitiy.   'Thread tools' button near the top.

BTW, using USB connections to storage for permanent storage access is problematic for a number of reasons.  Best to move to a connection type that uses screws like eSATA or infiniband, since even vibrations have causes USB connections to become loose.

---

