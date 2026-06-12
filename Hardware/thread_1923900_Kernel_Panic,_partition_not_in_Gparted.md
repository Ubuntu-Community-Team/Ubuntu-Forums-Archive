---
title: "Kernel Panic, partition not in Gparted?"
date: 2012-02-11
forum: Hardware
---

### Post by Goose306 on 2012-02-11
So, I've had a Wubi 11.10 install on Win7 for a few months now. Its dual-booted with Win7. Anywho, about two weeks ago I swapped in to Win7 for the first time in a few weeks and it ran a big chkdisk. I didn't think anything of it until I went to go back in to Ubuntu, and it went to grub and had a kernel panic. Trying "boot" or "boot linux" just said no kernel found. So I booted it up on a Live Disk, went in and the partition is no longer showing. I went in to Gparted and its missing in there too. I have a 500 GB hard-drive, and the 100 GB I had set aside for the Ubuntu system is missing from the total and not in Gparted either. 

I'm a bit lost where to proceed from here. I would like to keep the stuff on my initial Wubi install, but if its gone thats fine too. But I definitely need to recover that other 100 GB, but I don't want to run a full drive format because it would take a long time to wipe my Win7 system. Also, I have no idea why its not showing in Gparted. Even if it was corrupted, it would still be there I assume? A bit of a linux noob (been using it off and on for a few years) but I'm a bit confused on whats going on here. Any tips?

---

### Post by LinuxFan999 on 2012-02-11
Wubi is not recommended as a permanent installation.

Are you sure the other 100 GB of disk space is not visible in GParted?

I would recommend opening the disk utility and running a test on the disk to make sure it is okay. This can be done while running the Ubuntu live CD by searching for "disk utility" in the dash, then opening the utility, selecting the hard drive, then selecting "SMART Data" (make sure to check the bad sector count too). Next, select "run self test" and select the extended test (the extended test will take a while).

---

### Post by bcbc on 2012-02-12
If you're getting a kernel panic you should probably run fsck on the root.disk. (check the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F"))

A 100GB partition shouldn't disappear - are you sure it wasn't a virtual disk. But if you did have a partition and somehow windows repaired it out of existence, running '[testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")' can recover it. To install run and run:
```
sudo apt-get install testdisk
sudo testdisk
```

---

