---
title: "mtpfs problems in 12.10"
date: 2013-04-20
forum: Hardware
---

### Post by shochatd on 2013-04-20
I'm trying to find a way to transfer files from my Ubuntu 12.10 system to my Nexus 4, which wants to use MTP. I've read various articles on how to do this, most recently this one:
[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)
Here is the output I get when I try to give the mtpfs command (with the phone connected via USB):

[FONT=Courier New]
$mtpfs -o allow_other /mnt/nexus4
Listing raw device(s)
Device 0 (VID=18d1 and PID=4ee1) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   18d1:4ee1 @ bus 1, dev 7
Attempting to connect device
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Android device detected, assigning default bug flags
Listing File Information on Device with name: (NULL)
[/FONT]
Then, when I try to look at the mount point:

[FONT=Courier New]
$ ls /mnt/nexus4
ls: cannot access /mnt/nexus4: Transport endpoint is not connected
[/FONT]
Can anyone see what I'm doing wrong? I think the PTP_ERROR_IO is interesting since I'm not trying to use PTP.
-- David

---

