---
title: "hal update created problems"
date: 2008-10-18
forum: Hardware
---

### Post by nobodie on 2008-10-18
this is 8.04, intel P5N mobo, core2VTduo chip and ICH8. I run two HDD SATA, the first, 80GB with /boot,swap,/ and /home, the second is 320 GB with /sdb1, /sdb2, /sdb3 as partitions (documents storage, music storage and video storage). As well I use a 4GB Kingston flashdrive and a portable 30 GB 2.5" HDD that connect through USB. 

Got a rough picture? I usually don't have the USB stuff attached unless to up or down stuff for work or pleasure and carry them both about, details unimportant.

Since the recent update on hal about a week or 10 days ago (fuzzy calendar in head) i've had some USB problems especially with the USB HDD 30 GB drive (oh, both the flash and the HDD are vfat format). Here they are in order:

1) while the drive enclosure came with a backup power cube it usually hasn't needed it when plugging in to this computer. Suddenly after the update it won't run without it
2) often, sometimes, it won't be recognized. lsusb shows something connected but it doesn't recognize what it is even with the power cube, without external power it shows in lsusb but doesn't run or get recognized as external disk
3) on restart it sometimes recognizes it and sometimes doesn't. 
4) here is the kicker and the reason i finally wrote in. This morning i was cleaning house and, because i had been transferring files last night the USB HDD was plugged in. I am guessing that I hit a power cable while cleaning, but, for whatever reason the computer shut down. i didn't have time to worry about it, but a few minutes later went to check on why there wasn't any music. the hard drive indicator lights were on even though the computer was off, switch power on UPS off, unplug, still have lights. restart, no can do. confusion reigns with its cousin fear. then the revelation, disconnect the external HDD completely, lights out, plug in, restart, good to go.

obviously the power from the 30 GB HDD was feeding back to the main HDD drives (both lights for them showed them as on and active) but, well, i'm having a wtf moment with all this. it seems like potential big disaster and i'm not sure where to turn from here. If i hadn't had other problems with the hal update i wouldn't have immediately thought of hal, but it would seem that there is some connection, at the least because i have to use that pesky external power supply. 

suggestions, help, more information needed?
thanks

---

