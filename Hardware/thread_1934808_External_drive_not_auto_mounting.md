---
title: "External drive not auto mounting"
date: 2012-03-02
forum: Hardware
---

### Post by lifein3d on 2012-03-02
I've just switched back from Mint to Ubuntu and have done a clean install of 11.10.  I backed everything up on my Seagate external drive, which ran fine on Mint or Windows.  Now Ubuntu just isn't detecting it at all.  There's nothing in my filesystem/media folder, and when I did a fdisk -l there are just three listed, all sda's.  I can see in the forums instructions on how to manually mount the drive but they all start on the basis the drive is listed.  I know the USB port it's in is fine (runs the mouse and ran the drive there in Mint) and the external drive is okay (the data is visible on my windows PC and was fine this morning in Mint).  I can't see any threads about needing a driver, and since this same external drive worked in my earlier versions of Ubuntu before dabbling with Mint I didn't think it would need one.  I just don't know where to even start with this so any advice would be much appreciated.  This drive has everything on it and I'm really stuffed right now!  Thanks everyone.

---

### Post by athampan on 2012-03-02
Please pull out the cable and tail /var/log/messages and then plug the drive back in.  You should see errors or the name of the dev (/dev/sdb or something similar to that).  That should give you an idea how to move forward (better, please cut and paste the message here).

---

### Post by lifein3d on 2012-03-03
Thanks for getting back on this athampan.  I did what you said but I'm getting this:

tail: cannot open `/var/log/messages' for reading: No such file or directory

I went to a few sites to check my syntax ([http://linux.101hacks.com/unix/tail/](http://linux.101hacks.com/unix/tail/)) and I'm not sure why it's not adding up.  There is no file in the var/log called messages so I know what it means, I'm just not sure why.  

Sorry if that's a total noob question but I don't do much with terminal so I get stuck a lot easier than a knowledgeable person like yourself does.  Thanks for pointing me in the right direction.

---

### Post by athampan on 2012-03-03
You could alternatively run the command "dmesg" immediately after you plug your drive back into the USB port.

Also my bad ... this thread here: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8) says it's /var/log/syslog that you need to tail.

---

### Post by lifein3d on 2012-03-03
Great thanks athampan, got that working.  Gave me this:

Mar  3 18:39:26 duanes-laptop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar  3 18:44:25 duanes-laptop AptDaemon: INFO: Quitting due to inactivity
Mar  3 18:44:25 duanes-laptop AptDaemon: INFO: Quitting was requested
Mar  3 18:44:25 duanes-laptop dbus[521]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar  3 18:44:25 duanes-laptop AptDaemon: INFO: Initializing daemon
Mar  3 18:44:25 duanes-laptop dbus[521]: [system] Successfully activated service 'org.debian.apt'
Mar  3 18:44:25 duanes-laptop AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar  3 18:44:25 duanes-laptop AptDaemon.Trans: INFO: Simulate was called
Mar  3 18:44:25 duanes-laptop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/6c8acf849d67413aa93d46bc5393582c
Mar  3 18:44:27 duanes-laptop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1

Not sure what I'm looking at there but no /dev or /sdb in there.  It almost looks like it's running some other process in a loop?  The install finished fine with no errors so if they're related it didn't come up at the time of the install.  Any advice?  Cheers athampan.

---

### Post by lifein3d on 2012-03-03
Oh sorry, looks like that's a known error.  I'll dig into that thread and see what I can do.  Not sure if they're related issues but I guess it's worth fixing it to see.

---

### Post by athampan on 2012-03-03
When I plug my USB drive I get the following in:

(a) /var/log/syslog:
```

Mar  3 11:29:36 mylaptop vmunix: [15710.392499] usb 1-1.1: new high speed USB device using ehci_hcd and address 4
Mar  3 11:29:36 mylaptop vmunix: [15710.728152] usbcore: registered new interface driver uas
Mar  3 11:29:36 mylaptop vmunix: [15710.754937] Initializing USB Mass Storage driver...
Mar  3 11:29:36 mylaptop vmunix: [15710.755197] scsi6 : usb-storage 1-1.1:1.0
Mar  3 11:29:36 mylaptop vmunix: [15710.755399] usbcore: registered new interface driver usb-storage
Mar  3 11:29:36 mylaptop vmunix: [15710.755405] USB Mass Storage support registered.
Mar  3 11:29:37 mylaptop vmunix: [15711.753786] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 2GB    8.07 PQ: 0 ANSI: 2
Mar  3 11:29:37 mylaptop vmunix: [15711.755412] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar  3 11:29:37 mylaptop vmunix: [15711.758643] sd 6:0:0:0: [sdb] 3944448 512-byte logical blocks: (2.01 GB/1.88 GiB)
Mar  3 11:29:37 mylaptop vmunix: [15711.759189] sd 6:0:0:0: [sdb] Write Protect is off
Mar  3 11:29:38 mylaptop vmunix: [15712.223451]  sdb: sdb1
Mar  3 11:29:38 mylaptop vmunix: [15712.225362] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

(b) dmesg:
```

[15710.755405] USB Mass Storage support registered.
[15711.753786] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 2GB    8.07 PQ: 0 ANSI: 2
[15711.755412] sd 6:0:0:0: Attached scsi generic sg2 type 0
[15711.758643] sd 6:0:0:0: [sdb] 3944448 512-byte logical blocks: (2.01 GB/1.88 GiB)
[15711.759189] sd 6:0:0:0: [sdb] Write Protect is off
[15711.759195] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15711.759199] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[15711.761303] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[15712.223451]  sdb: sdb1
[15712.225352] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[15712.225362] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by lifein3d on 2012-03-03
Mine's totally different so I think I might run the install disc again and see what happens.  I haven't done much to it since installing so I don't have anything to lose.  Thanks for taking the time to help me. Cheers.

---

### Post by athampan on 2012-03-03
Good luck with your attempts.

---

