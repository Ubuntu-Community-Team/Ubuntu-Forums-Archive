---
title: "SATA-IDE converter not working anymore"
date: 2008-11-08
forum: Hardware
---

### Post by =OTS=G-Man on 2008-11-08
Hello, I have a SATA to IDE converter on one of my drives because I am out of IDE ports. Now the drive did show up during install and when I first few times i booted into Ubuntu, but then after doing all the updates the drive does not detect anymore. I know the device is functioning, because I can see the Drive detect in BIOS and in my Vista Install.

I have tried booting back into the first kernel but again it does not show up. I have noticed that during boot the loading screen has the back and forth progress bar going for about 3 minutes and during the last 2 minutes about I can see the activity light on the SATA-IDE converter solid for about 30-45 seconds then off and back on 3 times then system starts to boot with the normal actual loading progress bar but no drive. Unplugging that drive make Ubuntu boot A LOT faster and is at the back and forth progress for maybe 30 seconds.

I'm running 
Ubuntu 8.04.1, kernel 2.6.24-21-generic


Just noticed in my logs that there is an error message with sdb (if my Linux knowledge is right, that the drive (2nd SATA drive)) ad its only started a few boots ago, nothing like it for the first few boots.

Nov  8 17:08:06 don-desktop kernel: [  456.288939] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.288946] end_request: I/O error, dev sdb, sector 0
Nov  8 17:08:06 don-desktop kernel: [  456.288948] printk: 4 messages suppressed.
Nov  8 17:08:06 don-desktop kernel: [  456.288950] Buffer I/O error on device sdb, logical block 0
Nov  8 17:08:06 don-desktop kernel: [  456.288953] Buffer I/O error on device sdb, logical block 1
Nov  8 17:08:06 don-desktop kernel: [  456.288955] Buffer I/O error on device sdb, logical block 2
Nov  8 17:08:06 don-desktop kernel: [  456.288956] Buffer I/O error on device sdb, logical block 3
Nov  8 17:08:06 don-desktop kernel: [  456.289767] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.289770] end_request: I/O error, dev sdb, sector 0
Nov  8 17:08:06 don-desktop kernel: [  456.289772] Buffer I/O error on device sdb, logical block 0
Nov  8 17:08:06 don-desktop kernel: [  456.290172] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.290176] end_request: I/O error, dev sdb, sector 586114696
Nov  8 17:08:06 don-desktop kernel: [  456.290177] Buffer I/O error on device sdb, logical block 73264337
Nov  8 17:08:06 don-desktop kernel: [  456.290566] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.290569] end_request: I/O error, dev sdb, sector 586114696
Nov  8 17:08:06 don-desktop kernel: [  456.290570] Buffer I/O error on device sdb, logical block 73264337
Nov  8 17:08:06 don-desktop kernel: [  456.290991] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.290994] end_request: I/O error, dev sdb, sector 0
Nov  8 17:08:06 don-desktop kernel: [  456.290996] Buffer I/O error on device sdb, logical block 0
Nov  8 17:08:06 don-desktop kernel: [  456.291000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 17:08:06 don-desktop kernel: [  456.291002] end_request: I/O error, dev sdb, sector 8
Nov  8 17:08:06 don-desktop kernel: [  456.291004] Buffer I/O error on device sdb, logical block 1
Nov  8 17:08:06 don-desktop kernel: [  456.291006] Buffer I/O error on device sdb, logical block 2

looks like theres more for that boot but I can post full log if requested

Hope to find a fix, thats my main "data" drive and only major thing from keeping me from using windows :)

Thanks

---

### Post by =OTS=G-Man on 2008-11-08
Just wanted to add an update. After seeing the logs I decided to run a chkdsk /f on it in Vista that didn't help. Also I went to try installing Fedora 9 on the same system and it had trouble with that drive a well.

Could it be a kernel thing? or maybe a BIOS setting?

Thanks again

---

### Post by RJARRRPCGP on 2008-11-09
I would reconnect the HDD, repartition, reformat and try again.

---

### Post by =OTS=G-Man on 2008-11-11
Ive tried reconnecting and all the different jumper setting. but nothing. Cant really reformat or partition it because ,like I said, it's my main data drive for the XP setup (user profiles are on that drive) but theres nothing really out of the ordinary about the drive, just 1 Primary NTFS Partition for the whole drive. Windows has no problem reading it nore does BIOS.

---

