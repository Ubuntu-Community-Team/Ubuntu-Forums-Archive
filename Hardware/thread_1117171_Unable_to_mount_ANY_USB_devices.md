---
title: "Unable to mount ANY USB devices"
date: 2009-04-05
forum: Hardware
---

### Post by lonelypauly on 2009-04-05
Any USB device I plug into my Xubuntu 8.10 64bit system gives me the following message:

"Unable to mount "Device Name":
mount: only root can mount /dev/sdc1 on /media/Misc

Here is my fdisk -l:

Disk /dev/sdc: 2008 MB, 2008023040 bytes
1 heads, 62 sectors/track, 63256 cylinders
Units = cylinders of 62 * 512 = 31744 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       63257     1960959+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.


I have looked all over these and other linux forums, following various instructions but so far none have solved this problem.  This started happening after the very last update, although that might be coincidental.

Any help would be greatly appreciated...this problem has been driving me crazy!

Thanks

---

### Post by x22 on 2009-04-05
well, have you tried it?

sudo mount /dev/sdc1 /media/Misc

---

### Post by lonelypauly on 2009-04-05
Yes, when i input:

sudo mount /dev/sdc1 /media/Misc

I get:

mount point /media/Misc does not exist


There is no /Misc in /media when I just checked in the file system.  I don't understand why the usb thumb drive shows up on the desktop even though it "does not exist"

---

### Post by gluxon on 2009-04-05
Open up a terminal.

Type in

**sudo nautilus**

then... open up the /media folder, and create the MISC folder.

Now retry the mounting command as root.

I do this almost everyday so this does work, and I got the same error when I was a newbie.

---

### Post by gregdebonis on 2009-04-05
Or simply do that:

```

sudo mkdir /media/Misc
sudo mount /dev/sdc1 /media/Misc 

```

---

### Post by lonelypauly on 2009-04-05
Thanks for your help.  Somehow the ability to auto- mount a usb drive when it is plugged in as a normal user has been lost.  Any idea how to correct this?

Now I see this message when trying to mount a usb drive as root:

**NTFS signature is missing.**



Thanks!

---

