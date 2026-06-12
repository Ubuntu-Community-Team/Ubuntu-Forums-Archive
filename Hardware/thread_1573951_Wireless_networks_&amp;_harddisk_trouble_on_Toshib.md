---
title: "Wireless networks &amp; harddisk trouble on Toshiba T110"
date: 2010-09-13
forum: Hardware
---

### Post by nissarup on 2010-09-13
My Girlfriend have just gotten a Toshiba T110 laptop. Being my girlfriend she immediately wanted me to install OS X in it and failing that Linux.

After giving up on OS X, I downloaded the 10.04 Netbook edition and made an USB-key and she have been happy with it so far. There is one strange issue with Wireless networking though. It doesn't pick up all the networks I know are live. It can't find my Apple TimeCapsule which all my Macs can find, and Windows on the laptop has no trouble there either. Ubuntu does pick up one network, which I donøt know the password to, but the signal strength changes and I can't login.

I thought that issue might clear up after updating Ubuntu. But I thought I would install it to the build-in harddisk first. But when I run the install application I only get to choose the USB-drive. Right after choosing the keyboard layout it jumps to the "Prepare disk space" screen and it only shows /dev/sdb which is the USB-drive. I can't see where to change it to the build in drive.

In GParted I can see both drives and the build in drive is partitioned in 3 partitions called SYSTEM (400MB), WINDOWS (116,37GB) & PENDRIVE (116,12GB). All of them ntfs.
There is a small key at the PENDRIVE partition and I don't think I can change that partition.

How can I install to the build-in drive?

PS: I have used Ubuntu on a couple of servers for a few years, so I'm not afraid of using the terminal.

UPDATE: I just tried the same USB disk on an Acer Aspire D250 (I think) and it works perfectly there. All networks show up and the installer chooses the right disk.

Update 2: After trying to format the drive and getting some errors, I ****ed up the drive enough so that after a fe reboots I could fully format it and I could install as normal. Updates cleared up the trouble with Wifi too. So all is well.

---

