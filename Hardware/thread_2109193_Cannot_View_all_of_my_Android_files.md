---
title: "Cannot View all of my Android files"
date: 2013-01-26
forum: Hardware
---

### Post by Deucalion29710 on 2013-01-26
I am using 12.10 Gnome Remix, and I am using a ICS device which has no option for mass storage.  Instead it's a MTP device (Galaxy Reverb).  I can view some of the files on my SD card from a file manager in Ubuntu.  When I try to connect to the device via terminal I get the following output:

mtpfs -o allow_other /media/MOUNTPOINT
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung GT P7310/P7510/N7000/I9070/I9100/I9300 Galaxy Tab 7.7/10.1/S2/S3/Nexus/Note/Y.
   Found 1 device(s):
   Samsung: GT P7310/P7510/N7000/I9070/I9100/I9300 Galaxy Tab 7.7/10.1/S2/S3/Nexus/Note/Y (04e8:6860) @ bus 1, dev 13
Attempting to connect device
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0




Any ideas?  I may have botched my MTP in Ubuntu altogether.  I get no devices in gmtp either.

---

### Post by Deucalion29710 on 2013-01-28
For future users.....I solved this one with the help of a Facebooker in a Linux group.  The real solution can be found here:

[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

\\:D/\\:D/\\:D/

---

