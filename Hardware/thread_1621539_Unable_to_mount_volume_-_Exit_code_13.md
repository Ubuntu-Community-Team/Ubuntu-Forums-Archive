---
title: "Unable to mount volume - Exit code 13"
date: 2010-11-14
forum: Hardware
---

### Post by WinRiddance on 2010-11-14
Hi everyone. I've found similar posts which either didn't apply perfectly to this scenario or which involved a windows dual-boot system that I don't have. I'm experiencing this problem ever since I upgraded to Ubuntu 10.10 a few days ago. Here's the exact error message:

> Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00000000  size: 1024  usa_ofs: 0  usa_count: 65535: Invalid argument
Record 6 has no FILE magic (0x0)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.**I've attached some screenshots**, showing that the usb drive is being recognized by Gparted as well as the Disk Utility. I've included a screenshot of the initial error too:


This message appears when I plug the usb drive into my laptop (64 bit Ubuntu). Until a few days ago I had my 250 GB external USB drive tied permanently into the system via the **mnt** path (not media) along with permanent **???** adjustments in the boot file, causing the drive to be instantly recognized during the boot process, with all available administrative functions i.e. file access. This worked in Ubuntu 9.04 and 9.10 and 10.04 without a problem (same external usb drive all the way).

This is however the first time that I upgraded via the update manager as opposed to creating a new iso and making a fresh installation. I figured that I'd be safe if I waited a month past the release date. BUMMER !!! Anyway, I use this external drive all of the time, keep my backups on there as well. Can someone please help me out with this problem, I'd sure appreciate it. Thanks.

---

### Post by WinRiddance on 2010-11-15
**Someone ... Please ... ???**

Tried mounting via disk utility which generated the same error ...
Checked FSTAB, noticed missing entry, attempted to recreate mount point as before ... and ended up with identical error message as received from the disk utility and earlier, after plugging in the drive. Even worse, my system stopped responding altogether until I re-entered the FSTAB via the recovery console in order to remove the changes that I'd placed in the FSTAB file. I really need some help with this ... !!!  :(

Problem is also identical with this one here:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1577925&highlight=mount+exited+exit+code+13](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1577925&highlight=mount+exited+exit+code+13)

I've attached a couple of terminal screenshots as well. These show the messages that are being received when trying to use the ntfs fix tool from Ubuntu, as suggested to be used elsewhere in this forum. I already had the latest version installed, but running it didn't do me any good whatsoever.

---

### Post by WinRiddance on 2010-11-15
Couldn't attach those images to the edited response. Got them in this reply though. I do have WinXP Pro installed on a virtual box but the VB won't  recognize any of my USB ports which means that I can't use the chkdsk  option from the VB either. This really bites .... :(

I'll be checking the software updates next, hoping there'll be a magical solution there ...

---

### Post by dino99 on 2010-11-15
the first thing you should try to fix is under winblows:
- clean the system as much as you can
- defrag
- use ccleaner to built a better reg

then close and reboot under ubuntu. Again clean the system:
- clean, autoclean, autoremove
- check that you only use genuine ubuntu repos (synaptic repo tab), and maybe some trusted ppa
- install bleachbit & use it to clean the system
- run a fsck on next reboot: sudo shutdown now -R

**** note: run gparted to see if the partitions are ok (no warnings) but dont modify the partitions (if you need , boot on partedmagic)

---

### Post by WinRiddance on 2010-11-15
Thanks for your time, dino99.

I did make sure that I had the latest updates and that my system was as clean as I could make it. Tried Gparted and it recognizes the disk just fine (as does the disk utility and the mount manager). There was also a reference to HirensBootCD in this forum, for a boot disk with a mini version of WinXP which I tried as well. That **did** make some kind of a difference (by re-assigning NTFS user permissions) since the initial error message when trying to mount that external USB drive has now changed. Still not fixed though. Here's the link to that:

[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)  (Click on download, then last page)

Last but not least I went ahead and tried the **check** (repair) function of Gparted since the  drive wasn't mounted anyway ... but that resulted in more errors. Took  more screenshots of all of the results too.

BTW:  The drive _does show up_ in places/computer as well as in nautilus. When I right click for the context menu I can even "safely remove drive" which then removes the symbol for it. Right clicking on Properties tells me that the permissions for that drive can't be determined. Trying to mount as root doesn't work either.
(and yes, I do have the latest version of ntfsprogs installed)

Ooops, forgot to mention that I did install bleachbit via **sudo apt-get install bleachbit** (after reading up on it at SourceForge) which cleaned another 500+ MB off my system ... to include a total of 63 bleachbit errors, mostly related to Firefox, Thunderbird, and AMD64 issues/items.

.

---

### Post by CharlesA on 2010-11-15
The only thing I can really suggest is hooking it up to a Windows box and running chkdisk on it, as there aren't really any Linux tools to check NTFS partitions.

That would be the best place to start.

If you aren't sharing between Linux and Windows, I'd suggest using a different file system.

---

### Post by WinRiddance on 2010-11-15
Thanks. The only Windows access that I have is to a WinVista box which won't permit me to use chkdsk as I don't have the required permissions for whatever reason. I switched to Ubuntu exclusively about 18 months ago but at that time my wife and son still had Windows related backup files on their systems (dual boot for both of them) which is why I kept that external drive as an NTFS formatted disk ... being able to read/write Ubuntu as well as Windows files.

I'm beginning to think that my access problem is **directly related to the Ubuntu 10.10 upgrade**? In the past I've always installed Ubuntu from scratch. This was the first time that I didn't. That external drive was tied into my Ubuntu setup permanently so I'd have instant access to everything all of the time. It appears that the 10.10 upgrade hosed something which wasn't a problem for my 3 previous Ubuntu versions (that I'd installed from scratch). Also, I just noticed a little while ago that my VB symbol with WinXP and one of my Ubuntu Beta versions was missing too ... **simply vanished into thin air**. When I checked my installed software it wasn't just the symbol that was missing ... but the whole thing, VB with both installed Operating Systems. Nuts ... !!! :mad:

I don't seem to be getting anywhere so I've opened up a new thread, hoping that someone can help me _retrieve my data from that disk_ somehow, after which I'd be glad to reformat the entire thing. Well, thanks to anyone who tried to help ...

.

---

### Post by CharlesA on 2010-11-15
Vista should have no problems accessing the disk as long as it is seen in disk management.

---

